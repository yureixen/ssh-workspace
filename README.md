# SSH Workspace

A GitHub Actions workflow that instantly spins up a remote SSH workspace — accessible from anywhere, anytime.

## Use Cases

- Remote development from any device
- Running build scripts (e.g. kernel builds)
- Quick debugging in a clean Linux environment

## Environment

| Resource | Spec |
|----------|------|
| OS       | Ubuntu (latest) |
| CPU      | 2 cores |
| RAM      | 7 GB |
| Storage  | 14 GB |
| Max Duration | 6 hours |

## Requirements

- A GitHub account
- A terminal with SSH installed

## How to Use

To use this on your own account, **Fork** this repository.

1. Go to the **Actions** tab of your repository
2. Select the **SSH Debug Session** workflow
3. Click **Run workflow**
4. Open the running job and check the logs for the SSH command:
   ```
   ssh <session-id>@nyc1.tmate.io
   ```
5. Copy that command into your local terminal to connect

The session uses [tmate](https://tmate.io) to provide instant SSH access, with no setup required on the runner. It stays alive for up to 6 hours.
