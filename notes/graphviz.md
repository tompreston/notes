# Drawing graphs with Graphviz
Install `dot` with:

    apt install graphviz

Build the graph:

    dot -Tps graph1.gv -o graph1.ps
    dot -Tpng graph1.gv -o graph1.png

Example graph:

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

Fancy graph:

	digraph G {
		size ="4,4";
		main [shape=box]; /* this is a comment */
		main -> parse [weight=8];
		parse -> execute;
		main -> init [style=dotted];
		main -> cleanup;
		execute -> { make_string; printf}
		init -> make_string;
		edge [color=red]; // so is this
		main -> printf [style=bold,label="100 times"];
		make_string [label="make a\nstring"];
		node [shape=box,style=filled,color=".7 .3 1.0"];
		execute -> compare;
	}
