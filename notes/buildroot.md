# Buildroot
## Dependencies
Use `PKG_DEPENDENCIES` in .mk to express build-time dependencies (build order).
Use select in Config.in to choose trivial dependencies (libpng etc)
  - Don't send the user around the houses selecting these
Use "depends on" in Config.in to notify the user of some large dependency, think
  - Toolchain requirements
  - Major functional components like X11, Wayland
  - Also comment with why this dependency is needed. Maybe this package doesn't
    need it directly, but a "select"ed package does (and therefore cannot be
    selected before this dependency is set)
