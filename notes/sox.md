# sox
Create audio files with sox. The dash is "outfile".

Create 5s 1 channel sine wave:

    sox --null --type raw --bits 32 --channels 1 --rate 48000 \
        - synth 5 sine 100 n -50 > audio-8ch.raw

Create 5s 8 channel sine wave:

    sox \
        --null --type raw --bits 32 --channels 8 --rate 48000 \
        - synth 5 \
            sine 100 sine 200 sine 300 sine 400 \
            sine 500 sine 600 sine 700 sine 800 \
            gain -50 \
        > audio-1ch.raw

Playing with aplay:

    aplay -Dhw:0,0 --rate=48000 --channels=8 --format=S32_LE audio-8ch.raw
