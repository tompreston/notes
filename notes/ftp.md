# FTP
Connect:

    ftp -p -z secure transfer.domain.co.uk

Commands:

    ls
    cd
    get
    put
    help

Using wget:

    wget \
        --ftp-user='${FTP_USER}' \
        --ftp-pass='${FTP_PASS}' \
        "ftps://transfer.domain.co.uk:21/path/to/file"
