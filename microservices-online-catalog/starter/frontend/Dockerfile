FROM node:12-alpine as base
ENV NODE_ENV=production
WORKDIR /app
COPY package*.json ./
RUN npm install && npm cache clean --force
ENV PATH=/app/node_modules/.bin:$PATH

FROM base as dev
ENV NODE_ENV=development
WORKDIR /app
RUN npm install --only=development
CMD ["npm", "start"]

FROM base as build
ENV REACT_APP_CATALOG_MANAGEMENT_BASE_URL=http://localhost:8081
ENV REACT_APP_CUSTOMER_SUPPORT_BASE_URL=http://localhost:8082
WORKDIR /app
COPY . .
RUN npm run build

FROM nginx:stable-alpine as prod

COPY --from=build /app/build /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]