# Stage 1: Build React app
FROM node:18 AS builder
WORKDIR /app
COPY . .

EXPOSE 3000
RUN npm install && npm run build

# Stage 2: Serve using Nginx
FROM nginx:alpine
COPY --from=builder /app/dist /usr/share/nginx/html
COPY nginx.conf /etc/nginx/conf.d/default.conf
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
