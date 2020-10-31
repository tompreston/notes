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
