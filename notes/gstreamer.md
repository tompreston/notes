# Gstreamer
- https://gstreamer.freedesktop.org/documentation/tutorials/basic/gstreamer-tools.html

Some test patterns:

    gst-launch-1.0 videotestsrc ! videoconvert ! autovideosink
    gst-launch-1.0 videotestsrc pattern=11 ! videoconvert ! autovideosink
    gst-launch-1.0 videotestsrc ! videoconvert ! \
        tee name=t ! queue ! autovideosink \
                t. ! queue ! autovideosink

Play a file:

     gst-launch-1.0 playbin uri=file:///home/tpreston/file.mp4

Help:

    gst-inspect-1.0 playbin
