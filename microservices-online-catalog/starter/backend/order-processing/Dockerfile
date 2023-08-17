# base
FROM node:12-alpine as base
EXPOSE 8083
ENV NODE_ENV=production
WORKDIR /app
COPY package*.json ./
RUN npm install && npm cache clean --force
ENV PATH=/app/node_modules/.bin:$PATH

# Dev
FROM base as dev
ENV NODE_ENV=development
WORKDIR /app
RUN npm install --only=development
CMD ["nodemon", "./bin/www"]

# prod
FROM base as prod
WORKDIR /app
COPY . .
CMD ["node", "./app.js"]