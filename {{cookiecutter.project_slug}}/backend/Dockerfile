FROM node:11.1.0-alpine
ARG node_env=production

LABEL maintainer="Luca Perret <perret.luca@gmail.com>" \
      org.label-schema.vendor="Strapi" \
      org.label-schema.name="Strapi Docker image" \
      org.label-schema.description="Strapi containerized" \
      org.label-schema.url="https://strapi.io" \
      org.label-schema.vcs-url="https://github.com/strapi/strapi-docker" \
      org.label-schema.version=latest \
      org.label-schema.schema-version="1.0"

ENV NODE_ENV=${node_env}

WORKDIR /usr/src/api

RUN echo "unsafe-perm = true" >> ~/.npmrc \
    && npm install -g strapi@3.0.0-alpha.25.2 \
    && npm install -g pm2

COPY . ./
RUN chmod +x ./strapi.sh

EXPOSE 1337

HEALTHCHECK --interval=15s --timeout=5s --start-period=30s \
      CMD node /usr/src/api/healthcheck.js

CMD ["./strapi.sh"]