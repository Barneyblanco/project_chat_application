
FROM node:12.16.1-alpine3.9 as build

WORKDIR /client_app/

COPY package*.json /client_app/

RUN npm install

COPY . /client_app/

RUN npm run build



FROM nginx:1.17.8-alpine

COPY --from=build /client_app/build /usr/share/nginx/html/

RUN rm /etc/nginx/conf.d/default.conf

COPY nginx/nginx.conf etc/nginx/conf.d

EXPOSE 80

CMD ["/bin/bash", "-c", "nginx -g \"daemon off;\""]

