---
title: "Setting Up Obsidian Git on iOS without iSH* or Working Copy - Share & showcase"
source: "https://forum.obsidian.md/t/setting-up-obsidian-git-on-ios-without-ish-or-working-copy/97800"
author:
  - "[[Obsidian Forum]]"
published: 2025-03-07
created: 2025-09-04
description: "I read a few other posts but have found an easier way. The key difference between those posts and this one is a (I think) new feature in iSH and iOS. (Hence the * in the title - you need iSH for a few things, then you c…"
tags:
  - "clippings"
---
[pgardella](https://forum.obsidian.md/u/pgardella)

[Mar 7](https://forum.obsidian.md/t/setting-up-obsidian-git-on-ios-without-ish-or-working-copy/97800?u=codybontecou "Post date")

I read a few other posts but have found an easier way.

The key difference between those posts and this one is a (I think) new feature in iSH and iOS. (Hence the \* in the title - you need iSH for a few things, then you can delete it.) iSH now mounts your iSH filesystem into the iOS Files app, where you can access them from within the iOS environment.

*Note*: I’m assuming you know Git and Obsidian for this tutorial.

I’ll use ForceBru’s excellent tutorial as a basis for this tutorial.

## Tutorial

1. Create an Obsidian Vault and configure it to use Git (in this case, Github). There are many good tutorials for this.
2. Commit and push your vault to Github.
3. On your iOS device:
	1. Install Obsidian
	2. Install and enable the Obsidian Git plugin
	3. Add your name and email to the Author Name and Author Email fields in the Obsidian Git settings
	4. Create a Personal Access Token (aka PAT) on Github
	5. Create an empty *local* vault on iOS
	6. Install iSH from App Store
4. In the iOS Files app:
	1. Click on `Browse` in the lower right corner and, if necessary, click `< Browse` in the upper left until you get to the topmost `Browse` page.
	2. Click on `On My iPhone`
	3. Click on the `Obsidian` folder with the Obsidian logo on it
	4. You will see a folder with the name of the empty Vault you created above
	5. Delete that folder by long pressing on it and clicking `Delete` but *remember the name of the folder*.
5. In iSH command line (start the iSH app)
	1. install git:
		1. Update Alpine repos: `apk update`
		2. Install git: `apk add git`
		3. Change to your home directory `cd ~`
		4. Clone your git repository
			1. `git clone https://github.com/<username>/obsidian-git.git` -use your own repository URL from Github. You will need to use your username and the PAT you created above.
			2. (Optional) Run `ls -a` to see whether your files are there
6. In the iOS Files app:
	1. Click on `Browse` in the lower right corner and, if necessary, click `< Browse` in the upper left until you get to the topmost `Browse` page.
	2. Click on `iSH` and then `root`. You should see your newly cloned Vault git repo there. If you click on the repo, you should see all of your files. (If you do this, make sure you click `< root` in the upper left to get back to the correct level.
	3. Long press the folder which represents your git repo.
	4. Click `Move`
	5. Click `On My iPhone` in the upper left
	6. Click on the `Obsidian` folder with the Obsidian logo on it (which should be empty, or you skipped the `Delete` step above).
	7. Click on `Copy` in the upper right corner
	8. Wait for the copy to complete
	9. Long press the folder that was just copied, and select `Rename`. Type in the name of the folder you had here before, which is the name of the empty Vault you created.
7. In the Obsidian app:
	1. You should now see all of the files from your vault, although you may need to click on the show sidebar button in the upper left if all you see is `No file is open`.
	2. Click on the hamburger icon in the lower right (three horizontal lines)
	3. Click on `Open Git source control`
	4. This is the same Obsidian Git panel you have on your desktop.
8. (Optional) Delete the iSH app

After that, use Obsidian just like you do on your desktop to sync the files using Git. No more using iSH to push and pull files. It all happens in the Obsidian app.

This may be common knowledge these days, but I couldn’t find it when I searched this morning.

[Yurcee](https://forum.obsidian.md/u/Yurcee)

[Mar 7](https://forum.obsidian.md/t/setting-up-obsidian-git-on-ios-without-ish-or-working-copy/97800/2?u=codybontecou "Post date")

I just skimmed the contents of your write-up.  
Can you tell us why iSH is needed? Because you cannot initialize a repo with Git plugin? Maybe this write-up is for people with no PCs? I don’t quite understand.

4 months later

[karl](https://forum.obsidian.md/u/karl)

[Jun 22](https://forum.obsidian.md/t/setting-up-obsidian-git-on-ios-without-ish-or-working-copy/97800/4?u=codybontecou "Post date")

Just made an account to say-- thank you. I’ve been trying and failing to sync github vault on ios for days. This did the trick!

20 days later

[matti](https://forum.obsidian.md/u/matti)

[Jul 12](https://forum.obsidian.md/t/setting-up-obsidian-git-on-ios-without-ish-or-working-copy/97800/5?u=codybontecou "Post date")

Before going this route, make sure to read more about Obsidian Git’s experimental support for mobile platforms: [GitHub - Vinzent03/obsidian-git: Integrate Git version control with automatic commit-and-sync and other advanced features in Obsidian.md](https://github.com/Vinzent03/obsidian-git?tab=readme-ov-file#-mobile-support-%EF%B8%8F--experimental)

> The Git implementation on mobile is **very unstable**! I would not recommend using this plugin on mobile, but try other syncing services.

2 months later

[CodyBontecou](https://forum.obsidian.md/u/CodyBontecou)

[21m](https://forum.obsidian.md/t/setting-up-obsidian-git-on-ios-without-ish-or-working-copy/97800/6?u=codybontecou "Post date")

This worked like a charm. I made this account just to thank you. Getting Obsidian Git on iOS has been an inconsistent headache for me for quite sometime.

Thank you!

This topic is unpinned for you; it will display in regular order

  

### Want to read more? Browse other topics in Share & showcase or view latest topics.

[Powered by Discourse](https://discourse.org/powered-by)