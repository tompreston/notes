# vim
Install pathogen:

    mkdir -p ~/.vim/autoload ~/.vim/bundle && \
        curl -LSso ~/.vim/autoload/pathogen.vim https://tpo.pe/pathogen.vim

Add pathogen to .vimrc:

    execute pathogen#infect()

Install some useful extensions:

    cd ~/.vim/bundle
    git clone https://github.com/altercation/vim-colors-solarized
    git clone https://github.com/bogado/file-line.git
    git clone https://github.com/embear/vim-localvimrc
    git clone https://github.com/kergoth/vim-bitbake
    git clone https://github.com/tpope/vim-sensible.git
    git clone https://github.com/tpope/vim-surround.git

# vim-colors-solarized
I use GNOME terminal with the Solarized light colour scheme and Solarized
pallete. Be sure to set both to get correct colours.

# Some useful vim commands
Loop and printf

    :for i in range(0,1016,4) | put =printf('GIC_DIST_TARGET_%02X,0x50041%03x', i/4, i+0x800) | endfor

# Registers
- https://www.brianstorti.com/vim-registers/
- https://stackoverflow.com/a/3961954

Print registers:

    :reg

Normal yank is like "unnamed register + yank":

    ""y
    ""yy

Last yank is stored in "0 register. "1 to "9 are last deleted lines.

Clipboard is "+:

    "+y
    "+yy

See the currently loaded filetype:

    :set filetype?
    :set ft?
