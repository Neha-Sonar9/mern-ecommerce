FROM node:22-bookworm-slim AS builder
WORKDIR /app
copy package*.json ./
Run npm ci
COPY . .
RUN npm run build

FROM nginx:alpine 
RUN rm -rf /usr/share/nginx/html/*
WORKDIR /app
COPY --from=builder /app/build /usr/share/nginx/html

EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]