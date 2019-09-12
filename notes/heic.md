# High Efficiency Image File Format
- https://en.wikipedia.org/wiki/High_Efficiency_Image_File_Format
- https://photo.stackexchange.com/a/99405

Linux tool: ImageMagick 7.0.7-22 --with-libheif

    sudo dnf install ifuse libheif
    ifuse mnt
    heif-convert
    fusermount -u mnt
