FROM ubuntu:focal

ENV DEBIAN_FRONTEND=noninteractive

RUN apt update -y

RUN apt install -y npm

# Electron requirements
RUN apt install -y libgtk-3-0 libnotify4 libnss3 libxss1 libxtst6 \
  xdg-utils libatspi2.0-0 libdrm2 libgbm1 libxcb-dri3-0 trash-cli \
  libglib2.0-bin gvfs-bin pulseaudio
