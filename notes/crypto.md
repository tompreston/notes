# Cryptography (gnupg)
- Comprehensive Crypto Guide
  http://sanctum.geek.nz/arabesque/series/gnu-linux-crypto/
- Use subkeys and backup private master key
  https://wiki.debian.org/Subkeys?action=show&redirect=subkeys
- On GnuPG 1 vs 2 https://superuser.com/a/655250/240747

# Getting started

    gpg --gen-key
    gpg --list-secret-keys
    gpg --list-public-keys
    gpg --list-public-keys --keyid-format short

Provide someone with your public key:

    gpg --armor --export $KEYID > public-key.asc

Create a revocation certificate and store separately:

    gpg --output revoke.asc --gen-revoke $KEYID

Delete keys:

     gpg --delete-secret-key $KEYID
     gpg --delete-key $KEYID

# Signing

    echo "This is a public message from Tom" > message.txt
    gpg --clearsign message.txt
    cat message.txt.asc
    gpg --verify message.txt.asc

    tar -czf message.tar.gz message.txt
    gpg --armor --detach-sign message.tar.gz
    gpg --verify message.tar.gz.asc message.tar.gz

You can only verify using keys on your keyring. To import keys:

    wget http://www.apache.org/dist/httpd/KEYS
    gpg --import KEYS

# Encrypting messages

    echo "sssssh secret" > secret-message.txt
    gpg --armor --recipient $KEYID --encrypt secret-message.txt
    cat secret-message.txt.asc

Only the recipient can decrypt the message:

    gpg --decrypt secret-message.txt

We can also sign encrypted messages, to verify it came from us:

    gpg --armor --recipient $KEYID --sign --encrypt secret-message.txt


# Renewing expiry date
- https://superuser.com/a/1141251

    gpg --list-keys
    gpg --edit-key ${KEY_ID}
    gpg> expire
    gpg> key 1
    gpg> expire
    gpg> save

# Export and import
Export from backup:

    gpg --homedir=/tmp/gnupg-backup/.gnupg --export-secret-key ${KEY_ID} \
        > /tmp/key-id-secret-key.asc

Import to normal:

    gpg --import /tmp/key-id-secret-key.asc
