FROM node:14

WORKDIR /app

COPY package.json .

RUN npm install

COPY . .

ARG MY_ARG=3

ENV PORT 80

EXPOSE $PORT

# VOLUME ["/app/feedback"] # create an anonymous volume

CMD ["node", "server.js"]
