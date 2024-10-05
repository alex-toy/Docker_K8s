FROM node:14

WORKDIR /app

COPY package.json .

RUN npm install

COPY . .

EXPOSE 80

# VOLUME ["/app/feedback"] # create an anonymous volume

CMD ["node", "server.js"]
