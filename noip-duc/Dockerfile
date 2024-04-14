FROM ubuntu

# Install wget
RUN apt-get update \
  && apt-get install -y wget \
  && rm -rf /var/lib/apt/lists/*

WORKDIR /code

# Follow this: https://www.noip.com/support/knowledgebase/install-linux-3-x-dynamic-update-client-duc#install_from_source

## Download the Linux DUC
RUN wget https://dmej8g5cpdyqd.cloudfront.net/downloads/noip-duc_3.0.0.tar.gz

## Unpack it
RUN tar xf noip-duc_3.0.0.tar.gz

# Install it
RUN apt-get update \
  && apt-get install -y /code/noip-duc_3.0.0/binaries/noip-duc_3.0.0_armhf.deb \
  && rm -rf /var/lib/apt/lists/*

# Ideally should be done through https://docs.docker.com/reference/dockerfile/#run---mounttypesecret
ARG USER
ARG PASS
# Run noip-duc every 60 seconds
RUN watch -n 60 noip-duc -g all.ddnskey.com -u $USER -p $PASS
