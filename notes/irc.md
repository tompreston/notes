# IRC
List channel modes:

    /mode #channel

Remove or add modes:

    /mode +t
    /mode -t

Typical modes:
- https://freenode.net/kb/answer/channelmodes

# Clients
Hexchat does the job but irssi might be more compatible.

## Weechat
Some weechat config for light terminals:

    buflist.format.buffer_current        string   "${color:,blue}${format_number}${indent}${format_nick_prefix}${color:white,blue}${format_name}"
    buflist.format.hotlist_low           string   "${color:black}"
    fset.color.help_default_value        color    default
    fset.color.help_name                 color    default
    irc.color.item_channel_modes         color    white
    irc.server.codethink.addresses       string   "bouncer.codethink.co.uk/6502"
    irc.server.codethink.autoconnect     boolean  off
    irc.server.codethink.password        string   "${sec.data.codethink_password}"
    irc.server.codethink.ssl             boolean  on
    irc.server.codethink.username        string   "thomaspreston/codethink"
    irc.server.freenode.addresses        string   "bouncer.codethink.co.uk/6502"
    irc.server.freenode.password         string   "${sec.data.codethink_password}"
    irc.server.freenode.ssl              boolean  on
    irc.server.freenode.username         string   "thomaspreston/freenode"
    irc.server_default.nicks             string   "tpreston,tpreston1,tpreston2,tpreston3,tpreston4"
    irc.server_default.username          string   "tpreston"
    weechat.bar.buflist.items            string   "buflist"
    weechat.bar.fset.items               string   "fset"
    weechat.bar.title.color_fg           color    white
    weechat.color.chat_nick_self         color    black
    weechat.color.status_count_other     color    white
    weechat.color.status_data_other      color    white
    weechat.color.status_nicklist_count  color    white
    weechat.color.status_time            color    white
    weechat.look.mouse                   boolean  on
