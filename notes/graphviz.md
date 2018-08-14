# Drawing graphs with Graphviz
Draw directed graphs with Graphviz:

    digraph G {
        main -> parse -> execute;
        main -> init;
        main -> cleanup;
        execute -> make_string;
        execute -> printf
        init -> make_string;
        main -> printf;
        execute -> compare;
    }

Install `dot` with:

    apt install graphviz

Build the graph:

    dot -Tps graph1.gv -o graph1.ps
    dot -Tpng graph1.gv -o graph1.png
