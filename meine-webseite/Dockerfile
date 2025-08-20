# --- STAGE 1: Build ---
    FROM node:lts-alpine AS builder
    WORKDIR /app
    COPY package*.json ./
    RUN npm ci
    COPY . .
    RUN npm run build
    
    # --- STAGE 2: Serve ---
    FROM nginx:alpine
    COPY --from=builder /app/dist /usr/share/nginx/html
    EXPOSE 80
    HEALTHCHECK --interval=30s --timeout=10s --start-period=5s --retries=3 \
      CMD curl -f http://localhost/healthz.html || exit 1
    RUN echo "OK" > /usr/share/nginx/html/healthz.html