# Stage 1: Build Quasar SPA
FROM node:20-alpine AS builder

WORKDIR /app

# Copy ทุกอย่างเลย (ยกเว้นที่ระบุใน .dockerignore)
COPY . .

# Install dependencies
RUN npm ci --legacy-peer-deps

# Build Quasar (สำหรับ SPA)
RUN npm run build

# Stage 2: Production (Nginx serve static files)
FROM nginx:1.27-alpine

# Copy build artifacts จาก stage 1
COPY --from=builder /app/dist/spa /usr/share/nginx/html

# Create custom Nginx config inline สำหรับ SPA routing
RUN echo 'server { \
    listen 80; \
    server_name localhost; \
    root /usr/share/nginx/html; \
    index index.html; \
    location / { \
        try_files $uri $uri/ /index.html; \
    } \
}' > /etc/nginx/conf.d/default.conf

# Expose port
EXPOSE 80

# Run Nginx
CMD ["nginx", "-g", "daemon off;"]