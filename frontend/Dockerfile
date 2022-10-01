FROM node:13.12.0-alpine as build
WORKDIR /app
COPY package.json .
#COPY package-lock.json .
RUN npm install
COPY . .
RUN npm run build

FROM nginx:1.13.3-alpine
COPY --from=build /app/nginx/default.conf /etc/nginx/conf.d/
RUN rm -rf /usr/share/nginx/html/*
COPY --from=build /app/dist/shop /usr/share/nginx/html
