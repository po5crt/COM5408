FROM node:20-alpine AS builder

WORKDIR  /app

COPY package*.json ./

RUN npm ci

COPY  . .

FROM node:20-alpine

WORKDIR  /app
 
COPY --from=builder /app /node_modules./node_modules

COPY . .

RUN npm prune --production


RUN addgroup -S appgroup &&adduser -S appuser -G appgroup


USER node

EXPOSE 8080

CMD [ "node","index.js" ]


