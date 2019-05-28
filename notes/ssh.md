# SSH
- Use ED25519 instead of RSA https://ed25519.cr.yp.to/

Generate keys:

    ssh-keygen -t ed25519 -f ~/.ssh/tag_ed25519 -C tag

Copy to server:

    ssh-copy-id user@hostname

Debug ssh with:

    ssh -Tv git@gitlab.com
