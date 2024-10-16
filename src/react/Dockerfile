FROM node:20.18.0-alpine3.20 AS build
WORKDIR /usr/src/app
COPY . .

RUN npm install
RUN npm run build

EXPOSE 80