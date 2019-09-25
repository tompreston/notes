# FTP
Store details:

    cat > ~/.netrc <<EOF
    machine transfer.domain.co.yk
        login username
        password password
    EOF
    chmod 600 ~/.netrc

Connect:

    lftp transfer.domain.co.uk

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

But wget also understands ~/.netrc:

    wget --no-remove-listing ftps://transfer.domain.co.uk:21/
