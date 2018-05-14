FROM node:alpine

LABEL MAINTAINER="db@donbowman.ca"
LABEL taiga_version="branch:master"

ENV TAIGA_VERSION master

WORKDIR /taiga_events
COPY scripts/ /scripts/
# Getting from branch master, they don't provide tags, or stable branch
# https://github.com/taigaio/taiga-events/issues/8
ADD https://github.com/taigaio/taiga-events/archive/${TAIGA_VERSION}.tar.gz /taiga_events/

# See https://github.com/npm/uid-number/issues/3 for why the 'set unsafe-perm'
RUN tar -xzf ${TAIGA_VERSION}.tar.gz -C ./ taiga-events-master/ --strip-components=1 \
    && rm ${TAIGA_VERSION}.tar.gz \
    && npm config set unsafe-perm true \
    && npm i npm@latest -g \
    && npm install --production && npm install -g coffee-script \
    && addgroup -S taiga && adduser -S -G taiga taiga \
    && chown -R taiga /taiga_events \
    && chown -R taiga /scripts/ \
    && chmod +x /scripts/entrypoint.sh

USER taiga
ENTRYPOINT ["/scripts/entrypoint.sh"]
CMD ["coffee", "index.coffee"]
