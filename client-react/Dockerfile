# syntax=docker/dockerfile:1.5

FROM node:19.4-bullseye AS build

WORKDIR /usr/src/app

COPY package*.json ./

RUN npm install

COPY . .

RUN npm run build


FROM nginxinc/nginx-unprivileged:1.23-alpine-perl


COPY --link nginx.conf /etc/nginx/conf.d/default.conf

COPY --link --from=build usr/src/app/dist/ /usr/share/nginx/html

EXPOSE 8080