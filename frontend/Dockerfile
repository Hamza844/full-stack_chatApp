#----stage 1----
FROM node:alpine AS builder
WORKDIR /app
COPY package.json package-lock.json . /
RUN npm ci
ENV chatt=prodution
COPY . .
RUN npm run build
        #----stage 2----
#Dockerfile For Nginx webserver
FROM nginx:alpine
RUN rm -rf /usr/share/nginx/html/*
COPY --from=builder /app/dist /usr/share/nginx/html
COPY /nginx.conf /etc/nginx/conf.d/default.conf
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
