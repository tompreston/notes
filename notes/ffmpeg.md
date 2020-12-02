# ffmpeg
Encode for maximum compatibility [0]:

    ffmpeg -i <input> \
        -c:v libx264 -crf 23 -profile:v main \
        -pix_fmt yuv420p \
        -c:a aac -ac 2 -b:a 128k \
        -movflags faststart \
        output.mp4

Old devices don't support h.264 so use baseline level 3 instead of main:

        -profile:v baseline -level 3.0

[0] https://superuser.com/a/859075/240747

Trim videos:

    ffmpeg -ss 00:00:00 -t 00:30:00 -i input.avi -vcodec copy -acodec copy output1.avi

Concatenate videos:

    https://trac.ffmpeg.org/wiki/Concatenate

Add frame number to each frame (https://stackoverflow.com/a/15369938):

    ffmpeg \
        -i "$input" \
        -vf "drawtext=fontfile=Arial.ttf:
            text='%{frame_num}':
            start_number=1:
            x=(w-tw)/2:
            y=h-(2*lh):
            fontcolor=black:
            fontsize=20:
            box=1:
            boxcolor=white:
            boxborderw=5" \
        -c:a copy numbered.mov

Or show frame times using mpv. Use , and . to move frame by frame, you can see
the frame time on the CLI:

    mpv --osd-fractions video-240fps.mov

Dump the frames:

    ffmpeg -i numbered.mov "frames/%04d.jpg"
