# 1. Build stage
FROM node:24

WORKDIR /app

COPY package*.json ./
RUN npm install

COPY . .

RUN npm run build


# 2. Production stage (Nginx)
FROM nginx:alpine

COPY --from=builder /app/dist /usr/share/nginx/html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]