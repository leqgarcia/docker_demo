# syntax=docker/dockerfile:1
FROM node:12-alpine

RUN apk add --no-cache python g++ make
WORKDIR /app
COPY . .
RUN yarn install --production


EXPOSE 8080

CMD ["node", "src/index.js"]
