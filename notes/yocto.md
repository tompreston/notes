# Yocto
- https://elinux.org/Yocto_Project_Introduction

# Useful commands
List all recipes:

    bitbake-layers show-recipes
    bitbake-layers show-recipes $target

Run `do_compile`:

    bitbake $recipie-name -c compile

Enter a devshell before `do_compile`:

    bitbake $recipie-name -c devshell
