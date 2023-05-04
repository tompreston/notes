# git
Set aliases to move faster:

    git config --global alias.co checkout
    git config --global alias.br branch
    git config --global alias.ci commit
    git config --global alias.st status
    git config --global alias.di diff

Latest tag info:

    git describe

Short revs:

    git rev-parse --short HEAD

`git lg` https://coderwall.com/p/euwpig/a-better-git-log:

    git log --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit

`git send-email` https://www.freedesktop.org/wiki/Software/PulseAudio/HowToUseGitSendEmail/:

    git send-email --cover-letter --annotate master
    git format-patch --cover-letter -o outbox master

git am, "error: patch does not apply", try:

    git am --reject 0000-my-feature.patch

Statistics of a diff:

    git diff --stat SHA..HEAD

Get the branch name:

    git branch
    git rev-parse --abbrev-ref HEAD

What branch contains "string" in git log:

    $ git log --oneline --grep SOME_STRING $(git rev-list --all)
    561a28d updated to SOME_STRING

    $ git branch -a --contains 561a28d
        remotes/origin/the_magic_branch

Number of times an author has commited to a file:

    git blame --porcelain protoc-gen-typhon/generator.go | grep "author " | sort | uniq -ic | sort -n | head

List files in a commit:

    git diff-tree --no-commit-id --name-only -r HEAD

Shortest possible output with date (https://stackoverflow.com/a/1441062/2203114):

    git log --pretty=format:"%h%x09%an%x09%ad%x09%s"
