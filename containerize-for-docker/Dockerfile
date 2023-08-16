FROM node:16.17.1-alpine3.15
WORKDIR /app
COPY ./wait-for .
COPY ./backend .
ENV NODE_ENV=production
ENV JWT_SECRET=aaa967f1-2b08-4dde-a086-5df6bc8eff91
ENV JWT_EXPIRES_IN=604800
COPY ./frontend/build/ ./public
CMD ["npm", "start"]