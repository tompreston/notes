# Build mesa demos
# By using a developer workflow (bind-mount) changes can be made locally for
# debugging. Build environment is kept within container. Read index.html
# Author: Thomas Preston <thomas.preston@codethink.co.uk>
#
# Useful links:
# 	https://www.mesa3d.org/intro.html
# 	https://cgit.freedesktop.org/mesa/mesa
# 	https://01.org/linuxgraphics/community/mesa
#
# Create the image (from this dir):
#
# 	podman build -t mesa-demos containers/mesa-demos
#
# Download mesa-demos and build in the container:
#
#	git clone git://anongit.freedesktop.org/git/mesa/demos
#	podman run -it \
#	--mount=type=bind,src="$PWD/demos",dst=/mesa-demos \
#		mesa-demos
#
FROM debian:testing

# Install mesa-demos build env
ENV DEBIAN_FRONTEND=noninteractive
RUN apt-get update && apt-get install -y --no-install-recommends \
	autoconf \
	automake \
	build-essential \
	libtool \
	pkg-config
RUN apt-get update && apt-get install -y --no-install-recommends \
	freeglut3-dev \
	libglew-dev

WORKDIR /mesa-demos

CMD libtoolize && aclocal && autoconf && automake --add-missing && \
	autoreconf --install && ./configure && make
