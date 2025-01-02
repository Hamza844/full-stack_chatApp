FROM node:alpine 
WORKDIR /app
COPY package.json package-lock.json . /app
RUN npm ci
COPY . .
EXPOSE 5001
CMD ["npm", "start"]
