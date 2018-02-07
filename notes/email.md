# Email
To send email from laptop use the following configs.

    $ dpkg-reconfigure exim4-config

    $ tail -f /var/log/exim4/mainlog

    $ cat /etc/exim4/update-exim4.conf.conf
    dc_eximconfig_configtype='smarthost'
    dc_other_hostnames=''
    dc_local_interfaces='127.0.0.1 ; ::1'
    dc_readhost='domain.co.uk'
    dc_relay_domains=''
    dc_minimaldns='false'
    dc_relay_nets=''
    dc_smarthost='mail.domain.co.uk::587'
    CFILEMODE='644'
    dc_use_split_config='false'
    dc_hide_mailname='true'
    dc_mailname_in_oh='true'
    dc_localdelivery='mail_spool'

then edit /etc/exim4/passwd.client
    *.domain.co.uk:USERNAME:PASSWORD

    $ cat /etc/mailname
    ct-lt-586

    $ git config --global -l
    user.name=Thomas Preston
    user.email=thomas.preston@domain.co.uk
    core.editor=vim
    sendemail.from=Thomas Preston <thomas.preston@domain.co.uk>
    sendemail.envelopesender=thomas.preston@domain.co.uk
