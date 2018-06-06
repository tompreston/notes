# vim
Install pathogen:

    mkdir -p ~/.vim/autoload ~/.vim/bundle && \
        curl -LSso ~/.vim/autoload/pathogen.vim https://tpo.pe/pathogen.vim

Add pathogen to .vimrc:

    execute pathogen#infect()

Install some useful extensions:

    cd ~/.vim/bundle
    git clone https://github.com/tpope/vim-sensible.git
    git clone https://github.com/tpope/vim-surround.git
    git clone https://github.com/bogado/file-line.git

# Some useful vim commands
Loop and printf

    :for i in range(0,1016,4) | put =printf('GIC_DIST_TARGET_%02X,0x50041%03x', i/4, i+0x800) | endfor


