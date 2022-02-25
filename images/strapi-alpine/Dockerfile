# BASE
ARG NODE_VERSION=14
FROM node:${NODE_VERSION}-alpine AS base-alpine
EXPOSE 1337

FROM base-alpine

# RUN apk add --no-cache build-base gcc autoconf automake zlib-dev libpng-dev nasm bash

ARG STRAPI_VERSION=latest

# RUN yarn config set network-timeout 600000 -g
RUN yarn global add @strapi/strapi@${STRAPI_VERSION}


RUN mkdir -p /srv/app && chown 1000:1000 -R /srv/app

WORKDIR /srv/app

VOLUME /srv/app

COPY docker-entrypoint.sh /usr/local/bin/

RUN chmod 777 /usr/local/bin/docker-entrypoint.sh && ln -s /usr/local/bin/docker-entrypoint.sh

ENTRYPOINT ["docker-entrypoint.sh"]

CMD ["strapi"]
