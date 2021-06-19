# Wayland
Screen sharing requires pipewire:

    https://wiki.archlinux.org/index.php/PipeWire

In Chrome, you need to enable the setting:

    https://wiki.archlinux.org/index.php/PipeWire#WebRTC_screen_sharing

With this one:

    chrome://flags/#enable-webrtc-pipewire-capturer

I was able to get screen sharing with

    Fedora 33, Firefox 85, Jitsi, Google Meet
    Fedora 33, Chrome 88.0, Jitsi, Google Meet
    Debian 10, Chrome 88.0, Jitsi

I haven't tried:

     -enable-features=UseOzonePlatform -ozone-platform=wayland
