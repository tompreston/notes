# Using socat to chat!
You can use socat to chat on a localhost! Useful for when you don't have IRC
working etc.

Listen for connections:

    socat - TCP-LISTEN:12345

Connect as another user:

    socat - tcp:localhost:12345

Then just type and press enter. Some useful commands:

    ^G is terminal bell (not everyone has it on)
