# MMC
- https://elinux.org/images/9/91/Clement-sd-mmc-high-speed-support-in-linux-kernel_0.pdf

# Glossary
Term | Meaning
eMMC | embedded MMC, internal MMC card
SD   | Secur
SDIO | SD I/O device, like SD WiFi

# Useful commands
pv some.img | sudo dd of=/dev/mmcblk0 bs=4M conv=fsync
