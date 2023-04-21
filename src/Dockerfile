FROM node:12.16.3-alpine as build
WORKDIR '/app'

COPY package.json package.json
COPY package-lock.json package-lock.json
RUN npm ci
COPY . ./
RUN npm run build

FROM httpd:alpine
WORKDIR /var/www/html
COPY --from=build /app/build/ .