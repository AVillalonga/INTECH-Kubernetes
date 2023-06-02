FROM accetto/ubuntu-vnc-xfce-chromium-g3

USER root

RUN apt-get update -y && \
    apt-get upgrade -y && \
    apt-get install -y libgl1 apt-utils apt-transport-https software-properties-common gnupg curl iputils-ping vim libnss3-tools ssh git unzip && \
    apt-get update

# RUN apt-get update -y && \
#     apt-get upgrade -y && \
#     apt-get install -y apt-utils apt-transport-https software-properties-common gnupg curl iputils-ping vim libnss3-tools ssh git unzip && \
#     apt-get update

## Clean
RUN apt-get clean && \
    apt -y autoremove && \
    rm -rf /var/lib/apt/lists/*    

## Allow sudo without password
RUN echo "headless     ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers

## Remove desktop shortcut 
RUN rm /home/headless/Desktop/versionsticker.desktop

## Full size by default
RUN sed -i "s/UI.initSetting('resize', 'off');/UI.initSetting('resize', 'remote');/g" /usr/libexec/noVNCdim/app/ui.js

# Keep the connection alive to prevent timeouts
ENV NOVNC_HEARTBEAT=30

# USER headless
# RUN sudo mkdir /home/headless/work
# WORKDIR /home/headless/work

# /home/headless/albiononline/

# sudo docker run -p 6901:6901 --mount source=ao-vol,target=/home/headless/albiononline/ 