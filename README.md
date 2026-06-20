# ssh-workspace

A GitHub Actions workflow that instantly spins up a remote SSH workspace — accessible from anywhere, anytime.

## Use Cases

- Remote development from any device
- Running build scripts (e.g. kernel builds)
- Quick debugging in a clean Linux environment

## Environment

| Resource | Spec |
|----------|------|
| OS | Ubuntu (latest) |
| CPU | 2 cores |
| RAM | 7 GB |
| Storage | 14 GB |
| Max Duration | 6 hours |

## Requirements

- A GitHub account
- A terminal with SSH installed and [cloudflared](https://github.com/cloudflare/cloudflared/releases/latest) installed

## How to Use

To use this on your own account, **fork** this repository.

1. Generate an SSH key pair on your local machine if you don't have one:
   ```bash
   ssh-keygen -t ed25519 -N ""
   ```
2. Add your public key (`~/.ssh/id_ed25519.pub`) as a repository secret named `SSH_PUBLIC_KEY` under **Settings → Secrets and variables → Actions**
3. Go to the **Actions** tab of your repository
4. Select the **SSH Debug Session** workflow
5. Click **Run workflow**
6. Open the running job immediately and wait for the connect command to appear in the logs:
   ```
   ssh-keygen -R action-sshd-cloudflared && echo '...' >> ~/.ssh/known_hosts && ssh -o ProxyCommand='cloudflared access tcp --hostname https://xxxx.trycloudflare.com' runner@action-sshd-cloudflared
   ```
7. Copy the full command into your local terminal to connect

The session uses [action-sshd-cloudflared](https://github.com/valeriangalliat/action-sshd-cloudflared) to provide end-to-end encrypted SSH access over a Cloudflare Tunnel. It stays alive for up to 6 hours.
