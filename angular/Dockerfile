FROM node:10 as builder

WORKDIR /app

COPY . .

RUN npm install

RUN npm run build

FROM nginx
LABEL maintainer="joffrey mischler<jmischler72>"

COPY --from=builder /app/nginx/ /etc/nginx

COPY --from=builder /app/dist/* /usr/share/nginx/html

COPY --from=builder /app/entrypoint.sh /docker-entrypoint.d/entrypoint.sh
RUN chmod +x /docker-entrypoint.d/entrypoint.sh

