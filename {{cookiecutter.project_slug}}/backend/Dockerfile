FROM node:11.1.0-alpine
ARG node_env=production

WORKDIR /usr/src/api

RUN echo "unsafe-perm = true" >> ~/.npmrc \
    && npm install strapi@alpha -g

COPY . ./

ENV NODE_ENV=$node_env
RUN chmod +x ./strapi.sh

EXPOSE 1337

HEALTHCHECK --interval=15s --timeout=5s --start-period=30s \
      CMD node /usr/src/api/healthcheck.js

CMD ["./strapi.sh"]