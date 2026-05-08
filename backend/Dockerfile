FROM node:20-alpine AS builder
WORKDIR /app

# To install dependency
COPY package*.json ./
RUN npm ci --omit=dev

# Copy source and build
COPY . .
RUN npm run build


FROM node:20-alpine AS runtime
WORKDIR /app

# without the root 
RUN addgroup -S appgroup && adduser -S appuser -G appgroup

# To copy only and built artefacts + production node_modules
COPY --from=build /app/node_modules ./node_modules

USER appuser
EXPOSE 3000
CMD ["node", "server.js"]
