FROM node:20.18.0-alpine3.20 AS build
WORKDIR /usr/src/app
COPY . .

RUN mkdir app; npm install
RUN npm run build
RUN cp -r build/ app/host

# final
FROM nginx:1.17.1-alpine
COPY ./nginx.conf /etc/nginx/conf.d/default.conf
COPY --from=build /usr/src/app/app/host  /usr/share/nginx/html/host

EXPOSE 80