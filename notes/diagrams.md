# Drawing diagrams
* Create diagrams from textual descriptions
    * https://kroki.io/#cheat-sheet
    * https://kroki.io/examples.html

Use the kroki HTTP API:

    $ cat diagram.dot
    digraph G {
      Hello->World
    }

    $ curl https://kroki.io/graphviz/svg --data-binary '@diagram.dot' > diagram.svg
