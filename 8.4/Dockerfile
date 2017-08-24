FROM node:8.4

MAINTAINER Joel Caballero "joel@fiveanddone.com"

# Installing the 'apt-utils' package gets rid of the 'debconf: delaying package configuration, since apt-utils is not installed'
# error message when installing any other package with the apt-get package manager.
RUN apt-get update && DEBIAN_FRONTEND=noninteractive apt-get install -y --no-install-recommends \
    apt-utils \
 && rm -rf /var/lib/apt/lists/*

RUN apt-get update && DEBIAN_FRONTEND=noninteractive apt-get install -y --no-install-recommends \
    curl \
    apt-transport-https

# Configure Yarn repo and install
RUN curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | apt-key add -
RUN echo "deb https://dl.yarnpkg.com/debian/ stable main" | tee /etc/apt/sources.list.d/yarn.list
RUN apt-get update && apt-get install -y --no-install-recommends apt-utils\
    yarn


# Create app directory
RUN mkdir -p /usr/src/app
WORKDIR /usr/src/app

# replace this with your application's default port
EXPOSE 8888
# for webpack dev server
EXPOSE 8080
