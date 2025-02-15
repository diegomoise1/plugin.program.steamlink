# Use latest Raspberry Pi OS image based on debian:bookworm
FROM dtcooper/raspberrypi-os:latest

# Removed 'sudo' from commands as the base image runs as root
RUN apt-get update \
 && DEBIAN_FRONTEND=noninteractive apt-get --no-install-recommends install -y wget apt-transport-https \
 && apt-get update \
 && DEBIAN_FRONTEND=noninteractive apt-get --no-install-recommends install -y steamlink libgl1 libxv1 \
 && apt-get clean \
 && rm -rf /var/lib/apt/lists/*

# URL for the ARM64 version of the archive
RUN wget "http://media.steampowered.com/steamlink/rpi/bookworm/arm64/steamlink-rpi-bookworm-arm64-1.3.15.284.tar.gz" -O /tmp/steamlink.tgz

# Script to copy the needed libraries
COPY create_standalone_steamlink.sh /tmp/
RUN chmod a+x /tmp/create_standalone_steamlink.sh

ENTRYPOINT [ "/tmp/create_standalone_steamlink.sh" ]
