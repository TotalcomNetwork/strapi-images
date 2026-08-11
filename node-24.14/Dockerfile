FROM node:24.14-alpine

ENV ENV=prod

USER root
RUN apk add --no-cache \
            autoconf \
            automake \
            build-base \
            gcc \
            libpng-dev \
            nasm \
            python3 \
            py3-pip \
            tzdata \
            vips-dev \
            zlib-dev \
        && npm install --location=global --no-audit --fund=false create-strapi-app@latest \
        && mkdir -p /app

WORKDIR /app


ENTRYPOINT ["sh", "-c", "if [ ! -f \"/app/package.json\" ]; then npx --yes create-strapi-app@latest /app --quickstart --no-run --typescript && npm install --save --no-audit --fund=false mysql; fi && npm install --no-audit --fund=false && npm run build && if [ \"$ENV\" = \"dev\" ]; then npm run develop; else npm run start; fi"]


EXPOSE 1337
