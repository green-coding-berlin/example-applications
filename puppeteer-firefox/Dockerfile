FROM node:18-alpine3.15

# We need all the certificates to download the non-snap firefox
#COPY ./mozillateam-ubuntu-ppa.gpg /etc/apt/trusted.gpg.d/mozillateam-ubuntu-ppa.gpg
#COPY ./mozillateam-ubuntu-ppa-jammy.list /etc/apt/sources.list.d/mozillateam-ubuntu-ppa-jammy.list
#COPY ./mozilla-firefox-package.priority /etc/apt/preferences.d/mozilla-firefox
RUN apk add firefox

WORKDIR /var/www
COPY ./package.json /var/www/package.json
RUN npm i

# Container must run as the root user, otherwise we cannot connect to the Display.
# A more security concerned way would be to run the container with the user of the system

ENTRYPOINT [ "bash" ]
