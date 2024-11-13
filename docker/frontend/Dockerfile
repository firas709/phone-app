FROM node:20 AS build-stage

WORKDIR /app

COPY package*.json ./

RUN npm install

COPY ../../houri-phone-ui .

RUN npm run build --prod

FROM nginx:alpine

COPY ../../houri-phone-ui/nginx.conf /etc/nginx/nginx.conf

COPY --from=build-stage /app/dist/houri-phone-ui /usr/share/nginx/html

EXPOSE 80
