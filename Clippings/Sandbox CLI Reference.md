---
title: "Sandbox CLI Reference"
source: "https://vercel.com/docs/vercel-sandbox/cli-reference"
author:
  - "[[Vercel]]"
published:
created: 2025-11-17
description: "Based on the Docker CLI, you can use the Sandbox CLI to manage your Vercel Sandbox from the command line."
tags:
  - "clippings"
---
CLI Reference

Last updatedNovember 17, 2025

This page provides a complete reference for all available Vercel Sandbox CLI commands. The Sandbox CLI, based on the Docker CLI, allows you to manage sandboxes, execute commands, copy files, and more from the command line.

## sandbox --help

Get help information for all available sandbox commands:

terminal

```
sandbox <subcommand>
```

Description: Interfacing with Vercel Sandbox

Available subcommands:

- [`list`](https://vercel.com/docs/vercel-sandbox/#sandbox-list): List all sandboxes for the specified account and project. \[alias: `ls`\]
- [`create`](https://vercel.com/docs/vercel-sandbox/#sandbox-create): Create a sandbox in the specified account and project.
- [`copy`](https://vercel.com/docs/vercel-sandbox/#sandbox-copy): Copy files between your local filesystem and a remote sandbox \[alias: `cp`\]
- [`exec`](https://vercel.com/docs/vercel-sandbox/#sandbox-exec): Execute a command in an existing sandbox
- [`stop`](https://vercel.com/docs/vercel-sandbox/#sandbox-stop): Stop one or more running sandboxes \[aliases: `rm`, `remove`\]
- [`run`](https://vercel.com/docs/vercel-sandbox/#sandbox-run): Create and run a command in a sandbox
- [`login`](https://vercel.com/docs/vercel-sandbox/#sandbox-login): Log in to the Sandbox CLI
- [`logout`](https://vercel.com/docs/vercel-sandbox/#sandbox-logout): Log out of the Sandbox CLI

For more help, try running `sandbox <subcommand> --help`

## sandbox list

List all sandboxes for the specified account and project.

terminal

```
sandbox list [OPTIONS]
```

### Example

terminal

```
# List all running sandboxes

sandbox list

 

# List all sandboxes (including stopped ones)

sandbox list --all

 

# List sandboxes for a specific project

sandbox list --project my-nextjs-app
```

### Options

| Option | Alias | Description |
| --- | --- | --- |
| `--token <token>` | \- | Your Vercel authentication token. If you don't provide it, we'll use a stored token or prompt you to log in. |
| `--project <project>` | \- | The project name or ID you want to use with this command. |
| `--scope <team>` | `--team` | The team you want to use with this command. |

### Flags

| Flag | Short | Description |
| --- | --- | --- |
| `--all` | `-a` | Show all sandboxes, including stopped ones (we only show running ones by default). |
| `--help` | `-h` | Display help information. |

## sandbox run

Create and run a command in a sandbox.

terminal

```
sandbox run [OPTIONS] <command> [...args]
```

### Example

terminal

```
# Run a simple Node.js script

sandbox run -- node --version

 

# Run with custom environment and timeout

sandbox run --env NODE_ENV=production --timeout 10m -- npm start

 

# Run interactively with port forwarding

sandbox run --interactive --publish-port 3000 --tty npm run dev

 

# Run with auto-cleanup

sandbox run --rm -- python3 script.py
```

### Options

| Option | Alias | Description |
| --- | --- | --- |
| `--token <token>` | \- | Your Vercel authentication token. If you don't provide it, we'll use a stored token or prompt you to log in. |
| `--project <project>` | \- | The project name or ID you want to use with this command. |
| `--scope <team>` | `--team` | The team you want to use with this command. |
| `--runtime <runtime>` | \- | Choose between Node.js ('node22') or Python ('python3.13'). We'll use Node.js by default. |
| `--timeout <duration>` | \- | How long the sandbox can run before we automatically stop it. Examples: '5m', '1h'. We'll stop it after 5 minutes by default. |
| `--publish-port <port>` | `-p` | Make a port from your sandbox accessible via a public URL. |
| `--workdir <directory>` | `-w` | Set the directory where you want the command to run. |
| `--env <key=value>` | `-e` | Set environment variables for your command. |

### Flags

| Flag | Short | Description |
| --- | --- | --- |
| `--sudo` | \- | Run the command with admin privileges. |
| `--interactive` | `-i` | Run the command in an interactive shell. |
| `--tty` | `-t` | Enable terminal features for interactive commands. |
| `--rm` | \- | Automatically delete the sandbox when the command finishes. |
| `--help` | `-h` | Display help information. |

### Arguments

| Argument | Description |
| --- | --- |
| `<command>` | The command you want to run. |
| `[...args]` | Additional arguments for your command. |

## sandbox create

Create a sandbox in the specified account and project.

terminal

```
sandbox create [OPTIONS]
```

### Example

terminal

```
# Create a basic Node.js sandbox

sandbox create

 

# Create a Python sandbox with custom timeout

sandbox create --runtime python3.13 --timeout 1h

 

# Create sandbox with port forwarding

sandbox create --publish-port 8080 --project my-app

 

# Create sandbox silently (no output)

sandbox create --silent
```

### Options

| Option | Alias | Description |
| --- | --- | --- |
| `--token <token>` | \- | Your Vercel authentication token. If you don't provide it, we'll use a stored token or prompt you to log in. |
| `--project <project>` | \- | The project name or ID you want to use with this command. |
| `--scope <team>` | `--team` | The team you want to use with this command. |
| `--runtime <runtime>` | \- | Choose between Node.js ('node22') or Python ('python3.13'). We'll use Node.js by default. |
| `--timeout <duration>` | \- | How long the sandbox can run before we automatically stop it. Examples: '5m', '1h'. We'll stop it after 5 minutes by default. |
| `--publish-port <port>` | `-p` | Make a port from your sandbox accessible via a public URL. |

### Flags

| Flag | Short | Description |
| --- | --- | --- |
| `--silent` | \- | Create the sandbox without showing you the sandbox ID. |
| `--help` | `-h` | Display help information. |

## sandbox exec

Execute a command in an existing sandbox.

terminal

```
sandbox exec [OPTIONS] <sandbox_id> <command> [...args]
```

### Example

terminal

```
# Execute a simple command in a sandbox

sandbox exec sb_1234567890 ls -la

 

# Run with environment variables

sandbox exec --env DEBUG=true sb_1234567890 npm test

 

# Execute interactively with sudo

sandbox exec --interactive --sudo sb_1234567890 bash

 

# Run command in specific working directory

sandbox exec --workdir /app sb_1234567890 python script.py
```

### Options

| Option | Alias | Description |
| --- | --- | --- |
| `--token <token>` | \- | Your Vercel authentication token. If you don't provide it, we'll use a stored token or prompt you to log in. |
| `--project <project>` | \- | The project name or ID you want to use with this command. |
| `--scope <team>` | `--team` | The team you want to use with this command. |
| `--workdir <directory>` | `-w` | Set the directory where you want the command to run. |
| `--env <key=value>` | `-e` | Set environment variables for your command. |

### Flags

| Flag | Short | Description |
| --- | --- | --- |
| `--sudo` | \- | Run the command with admin privileges. |
| `--interactive` | `-i` | Run the command in an interactive shell. |
| `--tty` | `-t` | Enable terminal features for interactive commands. |
| `--help` | `-h` | Display help information. |

### Arguments

| Argument | Description |
| --- | --- |
| `<sandbox_id>` | The ID of the sandbox where you want to run the command. |
| `<command>` | The command you want to run. |
| `[...args]` | Additional arguments for your command. |

## sandbox stop

Stop one or more running sandboxes.

terminal

```
sandbox stop [OPTIONS] <sandbox_id> [...sandbox_id]
```

### Example

terminal

```
# Stop a single sandbox

sandbox stop sb_1234567890

 

# Stop multiple sandboxes

sandbox stop sb_1234567890 sb_0987654321

 

# Stop sandbox for a specific project

sandbox stop --project my-app sb_1234567890
```

### Options

| Option | Alias | Description |
| --- | --- | --- |
| `--token <token>` | \- | Your Vercel authentication token. If you don't provide it, we'll use a stored token or prompt you to log in. |
| `--project <project>` | \- | The project name or ID you want to use with this command. |
| `--scope <team>` | `--team` | The team you want to use with this command. |

### Flags

| Flag | Short | Description |
| --- | --- | --- |
| `--help` | `-h` | Display help information. |

### Arguments

| Argument | Description |
| --- | --- |
| `<sandbox_id>` | The ID of the sandbox you want to stop. |
| `[...sandbox_id]` | Additional sandbox IDs to stop. |

## sandbox copy

Copy files between your local filesystem and a remote sandbox.

terminal

```
sandbox copy [OPTIONS] <SANDBOX_ID:PATH> <SANDBOX_ID:PATH>
```

### Example

terminal

```
# Copy file from local to sandbox

sandbox copy ./local-file.txt sb_1234567890:/app/remote-file.txt

 

# Copy file from sandbox to local

sandbox copy sb_1234567890:/app/output.log ./output.log

 

# Copy directory from sandbox to local

sandbox copy sb_1234567890:/app/dist/ ./build/
```

### Options

| Option | Alias | Description |
| --- | --- | --- |
| `--token <token>` | \- | Your Vercel authentication token. If you don't provide it, we'll use a stored token or prompt you to log in. |
| `--project <project>` | \- | The project name or ID you want to use with this command. |
| `--scope <team>` | `--team` | The team you want to use with this command. |

### Flags

| Flag | Short | Description |
| --- | --- | --- |
| `--help` | `-h` | Display help information. |

### Arguments

| Argument | Description |
| --- | --- |
| `<SANDBOX_ID:PATH>` | The source file path (either a local file or sandbox\_id:path for remote files). |
| `<SANDBOX_ID:PATH>` | The destination file path (either a local file or sandbox\_id:path for remote files). |

## sandbox login

Log in to the Sandbox CLI.

terminal

```
sandbox login
```

### Example

### Flags

| Flag | Short | Description |
| --- | --- | --- |
| `--help` | `-h` | Display help information. |

## sandbox logout

Log out of the Sandbox CLI.

terminal

```
sandbox logout
```

### Example

terminal

```
# Log out of the Sandbox CLI

sandbox logout
```

### Flags

| Flag | Short | Description |
| --- | --- | --- |
| `--help` | `-h` | Display help information. |

---