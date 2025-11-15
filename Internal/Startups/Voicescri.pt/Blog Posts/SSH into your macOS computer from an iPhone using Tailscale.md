# SSH into your macOS computer from an iPhone using Tailscale

> Bring the power of agentic coding to your mobile device using a few basic, free tools.

I tend to tinker with my development environment even when I’m away from my desk. My iPhone has become a surprisingly capable terminal. Even with nothing but the on‑screen keyboard, I can browse code, run scripts and deploy updates from a café. Tailscale ties it all together by creating a secure, mesh‑style VPN between my devices. Below is my workflow for securely SSHing into my Mac from an iPhone using Tailscale.

## Why Tailscale?

Tailscale sits on top of WireGuard® and automatically creates a private network (a **tailnet**) between all your devices. Once everything is connected, each device gets a stable private IP and a human‑readable `device.ts.net` hostname via MagicDNS. The service also offers a built‑in SSH server (called **Tailscale SSH**) which manages SSH keys for you and even prompts for device‑level approval when you connect.

However, there is an important nuance on macOS: Tailscale ships **three different variants**. Only the **open‑source `tailscaled` variant** can act as a Tailscale SSH server; the App Store and standalone variants can be SSH clients but cannot host Tailscale SSH sessions[tailscale.com](https://tailscale.com/kb/1065/macos-variants#:~:text=Minimum%20macOS%20macOS%2012,SSH%20client%20yes%20yes%20yes). If you prefer to use macOS’s built‑in SSH daemon, the standalone variant works fine. The steps below cover both approaches.

## 1 – Prepare your Mac

1. **Install Tailscale.** Head to tailscale.com/download and install either the standalone Mac client or the open‑source variant. The docs explain that only the open‑source `tailscaled` can be a Tailscale SSH server, while the other variants are limited to client functionality[tailscale.com](https://tailscale.com/kb/1065/macos-variants#:~:text=Minimum%20macOS%20macOS%2012,SSH%20client%20yes%20yes%20yes).
    
2. **Sign in.** Launch Tailscale and follow the login flow to register your Mac to your tailnet. Tailscale will assign a `100.x.x.x` IP and a hostname like `my‑macbook.ts.net`.
    
3. **Enable SSH on macOS.** If you plan to use the built‑in SSH daemon instead of Tailscale SSH, enable “Remote Login” in System Settings → **General → Sharing**. On macOS Ventura and later the steps are:
    
    - Go to **Apple Menu → System Settings**.
        
    - In the sidebar, click **General**, then scroll down to **Sharing**[helpwire.app](https://www.helpwire.app/blog/mac-remote-access-software/#:~:text=How%20to%20Access%20a%20Mac,Remotely%20with%20Remote%20Login).
        
    - Turn on **Remote Login** and choose whether to allow all users or only specific users[helpwire.app](https://www.helpwire.app/blog/mac-remote-access-software/#:~:text=1,it%20to%20the%20other%20devices). macOS displays an `ssh username@hostname` command – save this; you’ll need the username later[helpwire.app](https://www.helpwire.app/blog/mac-remote-access-software/#:~:text=1,Login%20for%20Mac%20remote%20access).
        
4. **(Optional) Enable Tailscale SSH.** If you installed the open‑source variant, you can offload key management to Tailscale. Run this one‑time command in Terminal:
    
    `sudo tailscale set --ssh`
    
    Tailscale will generate a host key pair, share the public key with the control plane and intercept port 22 traffic from your tailnet[tailscale.com](https://tailscale.com/kb/1193/tailscale-ssh#:~:text=To%20enable%20Tailscale%20SSH%2C%20you,must). You must ensure your tailnet ACLs permit SSH access; the default policy usually does[tailscale.com](https://tailscale.com/kb/1193/tailscale-ssh#:~:text=To%20enable%20Tailscale%20SSH%2C%20you,must).
    

## 2 – Install Tailscale on your iPhone

1. **Download the Tailscale app** from the App Store and log in with the same account you used on your Mac. After logging in, you should see your iPhone and Mac listed as nodes within the same tailnet[yoshixi.dev](https://yoshixi.dev/posts/ja-20250628-how-to-ssh-into-mac-from-iphone/#:~:text=Install%20the%20Tailscale%20app%20from,network%2C%20which%20is%20called%20tailnet).
    

## 3 – Connect using an iOS SSH client

You’ll need an SSH client on your iPhone. I like **Termius** and **Blink Shell**, but any iOS SSH client works.

### Using Termius

1. Install **Termius** from the App Store.
    
2. Open Termius, go to the **Vault** tab and tap the **+** button to add a new host[yoshixi.dev](https://yoshixi.dev/posts/ja-20250628-how-to-ssh-into-mac-from-iphone/#:~:text=Install%20Termius%20on%20your%20iPhone,to%20your%20Mac%20via%20SSH).
    
3. Fill in the connection details:
    
    - **Label:** A friendly name like “My MacBook Pro”.
        
    - **Hostname:** Use your Mac’s Tailscale IP (e.g. `100.101.33.15`) or MagicDNS name (e.g. `my‑macbook.ts.net`)[yoshixi.dev](https://yoshixi.dev/posts/ja-20250628-how-to-ssh-into-mac-from-iphone/#:~:text=In%20Termius%2C%20you%20can%20add,Enter%20the%20following%20information).
        
    - **Username:** Your macOS username (run `whoami` on your Mac if unsure)[yoshixi.dev](https://yoshixi.dev/posts/ja-20250628-how-to-ssh-into-mac-from-iphone/#:~:text=In%20Termius%2C%20you%20can%20add,Enter%20the%20following%20information).
        
    - **Password:** If you’re using macOS’s SSH server, enter your Mac password. If you enabled Tailscale SSH, leave the password field blank; Tailscale will handle authentication and prompt you to approve the connection on your devices.
        
4. Save the host and initiate the connection. When connecting via Tailscale SSH, you’ll receive a push notification from the Tailscale app asking you to approve the new SSH session. Approve it and Termius will drop you straight into your Mac’s shell.
    

### Using Blink Shell

1. Install **Blink Shell** from the App Store.
    
2. Run `ssh username@my‑macbook.ts.net` in the terminal. Blink will prompt for your password if you’re using macOS’s SSH server, or launch a web‑based approval if you’re using Tailscale SSH.
    

## 4 – Automate the connection with iOS Shortcuts

I often forget to open Tailscale before launching my SSH client. Fortunately, the Tailscale app integrates with Apple’s Shortcuts app so you can automate connecting to your tailnet.

To create a shortcut that automatically connects to your tailnet when you join a specific Wi‑Fi network:

1. **Launch Shortcuts** and tap the **Automation** tab.
    
2. Tap **＋**, then select **Create Personal Automation**.
    
3. Choose **Wi‑Fi** and select the network where you want the automation to run (for example, your home or a coffee shop). Tap **Next**.
    
4. Tap **Add Action**, scroll to the **Tailscale** app section and choose **Connect**[tailscale.com](https://tailscale.com/kb/1233/mac-ios-shortcuts#:~:text=1,Select%20Done). This action instructs Tailscale to connect to your tailnet when the automation triggers.
    
5. (Optional) Tap **Add Action** again and select **Open App**, then choose your preferred SSH client (e.g. Termius) so it launches after Tailscale connects.
    
6. Tap **Next**, then **Done** to save the automation.
    

Now, whenever your iPhone joins the selected Wi‑Fi network, it will automatically connect to your tailnet and launch your SSH client. You can also run the shortcut manually from the Shortcuts app or via the home screen widget.

## Tips and tricks

- **MagicDNS:** Enabling MagicDNS in your Tailscale admin panel lets you use `device.ts.net` hostnames instead of numeric IPs. It’s easier to remember and follows you if your device’s IP changes.
    
- **Shortcuts integration:** Use the Shortcuts app to automate Tailscale. For example, you can create a personal automation that connects to your tailnet when your phone joins a specified Wi‑Fi network, then opens your SSH client[tailscale.com](https://tailscale.com/kb/1233/mac-ios-shortcuts#:~:text=1,Select%20Done). This ensures you don’t forget to start Tailscale before beginning your session.
    
- **Security:** When you enable Remote Login, you’re exposing your shell. Use strong passwords and restrict which users can log in[helpwire.app](https://www.helpwire.app/blog/mac-remote-access-software/#:~:text=By%20allowing%20remote%20access%20to,your%20system%20and%20data%20safety). If you’re comfortable with Tailscale SSH, it avoids storing passwords on clients and can require per‑session approval.
    
- **Offline approvals:** If you’re away from your Mac, enable **Touch ID** or **Face ID** on your iPhone to quickly approve SSH requests[helpwire.app](https://www.helpwire.app/blog/mac-remote-access-software/#:~:text=,Mac%20account%20on%20mobile%20devices).
    

## Final thoughts

This setup has been a game changer for me. I no longer drag my laptop to every coffee shop; instead, my iPhone can update dependencies, push commits or run AI experiments using its virtual keyboard. Tailscale’s peer‑to‑peer mesh means I don’t need to punch holes in my router or memorize obscure IP addresses. With a bit of configuration—installing Tailscale, enabling Remote Login on macOS, and configuring Termius—you can securely shell into your Mac from anywhere.

Let me know if you try it and how it goes. Happy remote hacking!