# LaTeX
My preferred method of using LaTeX is with pandoc in a Docker container. You can
use `jagregory/pandoc` as if it is the `pandoc` command itself:

    docker run -v $PWD:/source jagregory/pandoc doc.md -o doc.pdf

You can make presentations with the **beamer** theme. GUADEC has some decent
templates:

    https://gitlab.gnome.org/GNOME/presentation-templates
