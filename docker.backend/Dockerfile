FROM node:20-alpine AS builder

WORKDIR /app

# Copy dependency files
COPY package.json package-lock.json ./

# Install dependencies
RUN npm ci

# Copy application source
COPY . .

# -----------------------------
# Production image
# -----------------------------
FROM node:20-alpine

WORKDIR /app

# Copy only built app + node_modules from builder
COPY --from=builder /app ./

# Remove dev dependencies
RUN npm prune --production

# Create non-root user
RUN addgroup -S appgroup && adduser -S appuser -G appgroup

USER appuser

EXPOSE 8080

CMD ["node", "index.js"]


