# tmux
- https://www.hamvocke.com/blog/a-quick-and-easy-guide-to-tmux
- https://www.hamvocke.com/blog/a-guide-to-customizing-your-tmux-conf

# tmux in gnome-terminal
You have to set the right term info:

    gnome-terminal --preferences
    profile > edit > command > tick "run a custom command instead of my shell"

Set either:

    env TERM=gnome-256color /bin/bash
    env TERM=gnome-256color /usr/bin/tmux

This fixes:

    https://github.com/tmux/tmux/issues/459
