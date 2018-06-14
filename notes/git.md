# git
Latest tag info

    git describe

Short revs

    git rev-parse --short HEAD

`git lg` https://coderwall.com/p/euwpig/a-better-git-log

    git log --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit


`git send-email` https://www.freedesktop.org/wiki/Software/PulseAudio/HowToUseGitSendEmail/

    git send-email --cover-letter --annotate master
    git format-patch --cover-letter -o outbox master

git am, "error: patch does not apply", try:

    git am --reject 0000-my-feature.patch
