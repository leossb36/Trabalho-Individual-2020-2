ARG NODE_IMAGE_VERSION=12-alpine
ARG NGINX_IMAGE_VERSION=1.19-alpine

FROM node:${NODE_IMAGE_VERSION} as development-stage

WORKDIR /app

COPY package*.json ./

RUN yarn global add @vue/cli \
    && yarn global add @quasar/cli

COPY . .

FROM development-stage as build-stage

RUN yarn

RUN quasar build

FROM nginx:${NGINX_IMAGE_VERSION} as production-stage

COPY --from=build-stage /app/dist/spa /usr/share/nginx/html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
