# Graphics
There are several confusing components:

- "Window management" APIs (hardware level):
    - Wayland (new) OpenGL, EGL, libEGL.so
    - X11 (old) to OpenGL, GLX, libGLX.so
- Khronos Group rendering APIs (for 3D graphics):
    - Desktop, OpenGL, libGL
    - Embedded, OpenGL ES, libGLESv1.so libGLESv2.so

Hardware video acceleration (VA) (video decoding) uses separate hardware to 3D
graphics. Libraries involved:
- VA-API libva (Intel developed open standard)
- VDPAU (NVIDIA)

Both GL and VA use DRI to draw to to windows.
