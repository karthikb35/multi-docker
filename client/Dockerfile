FROM node:alpine as builder
WORKDIR '/app'
COPY ./package.json ./
RUN npm install
COPY . .
RUN npm run build

FROM niginx
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginnx/conf.d/default.conf
COPY --from=builder /app/build /usr/share/nginx/html