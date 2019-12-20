FROM node:13.5.0

RUN npm install -g laravel-echo-server

EXPOSE 6001

WORKDIR /

COPY laravel-echo-server.json .

CMD ["laravel-echo-server", "start"]