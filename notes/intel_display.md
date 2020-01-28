# intel display debugging
- https://www.mesa3d.org/envvars.html

Environmnets:

    vblank_mode=0 # render as fast as you can
    INTEL_DEBUG=buf

DRM debug:

    drm.debug=0x05
    echo 0x05 > /sys/module/drm/parmaters/debug
