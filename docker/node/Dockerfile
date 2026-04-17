FROM node:24-alpine

RUN corepack enable && corepack prepare pnpm@latest --activate

ARG UID=1000
ARG GID=1000
RUN deluser --remove-home node \
    && addgroup -g ${GID} app \
    && adduser -D -u ${UID} -G app -h /home/app app \
    && mkdir -p /home/app/.local/share/pnpm/store /home/app/.cache \
    && chown -R app:app /home/app

ENV HOME=/home/app \
    PNPM_HOME=/home/app/.local/share/pnpm \
    PATH=/home/app/.local/share/pnpm:$PATH

WORKDIR /var/www/html

USER app
