# base
FROM node:12-alpine as base
EXPOSE 8081
ENV NODE_ENV=production
WORKDIR /app
COPY package*.json ./

# the following command was requested by tutorial. However, local node version differs from base image
# and was failing. Solution: use node:16-alpine instead or npm install instead
# RUN npm ci && npm cache clean --force
RUN npm install && npm cache clean --force
ENV PATH=/app/node_modules/.bin:$PATH

# Dev
FROM base as dev
ENV NODE_ENV=development
WORKDIR /app
RUN npm install --only=development
CMD ["nodemon", "./app.js"]

# prod
FROM base as prod
WORKDIR /app
COPY . .
CMD ["node", "./app.js"]