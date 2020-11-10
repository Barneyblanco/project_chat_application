FROM node

WORKDIR /client_app/

COPY package*.json /client_app

RUN npm install

COPY . /client_app/

RUN npm run build

FROM nginx

COPY --from=build /client_app/build /usr/share/nginx/html/

RUN rm /etc/nginx/conf.d/default.conf

COPY nginx/nginx.conf etc/nginx/conf.d

EXPOSE 80

CMD ["/bin/bash", "-C", "nginx-g\"daemon off;\""]



