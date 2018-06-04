# Some useful vim commands
Install pathogen:

    mkdir -p ~/.vim/autoload ~/.vim/bundle && \
        curl -LSso ~/.vim/autoload/pathogen.vim https://tpo.pe/pathogen.vim

Some useful extensions:

    ls ~/.vim/bundle/
    file-line  vim-{sensible,surround}

Loop and printf

    :for i in range(0,1016,4) | put =printf('GIC_DIST_TARGET_%02X,0x50041%03x', i/4, i+0x800) | endfor
