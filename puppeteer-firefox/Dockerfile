FROM ubuntu:22.04
RUN apt-get update && apt-get install curl ca-certificates -y
RUN curl -fsSL https://deb.nodesource.com/setup_18.x | bash -

COPY ./mozillateam-ubuntu-ppa.gpg /etc/apt/trusted.gpg.d/mozillateam-ubuntu-ppa.gpg
COPY ./mozillateam-ubuntu-ppa-jammy.list /etc/apt/sources.list.d/mozillateam-ubuntu-ppa-jammy.list
COPY ./mozilla-firefox-package.priority /etc/apt/preferences.d/mozilla-firefox
RUN apt-get update && apt-get install -y nodejs firefox 

WORKDIR /var/www
COPY ./package.json /var/www/package.json
RUN PUPPETEER_PRODUCT=firefox npm i

# Container must run as the root user, otherwise we cannot connect to the Display.
# A more security concerned way would be to run the container with the user of the system

ENTRYPOINT [ "bash" ]
