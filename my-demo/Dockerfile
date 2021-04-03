FROM nginx:latest

COPY ./nginx.conf /etc/nginx/nginx.conf
COPY ./default.conf /etc/nginx/conf.d/default.conf
COPY ./html /usr/share/nginx/html

WORKDIR /app

## add permissions for nginx user
RUN chown -R nginx:nginx /app && chmod -R 755 /app && \
        chown -R nginx:nginx /var/cache/nginx && \
        chown -R nginx:nginx /var/log/nginx && \
        chown -R nginx:nginx /etc/nginx/conf.d
RUN touch /var/run/nginx.pid && \
        chown -R nginx:nginx /var/run/nginx.pid

RUN mkdir -p /var/nginx/log/

USER nginx

CMD sed -i -e 's/PORT/'"$PORT"'/g' /etc/nginx/conf.d/default.conf &&nginx -g 'daemon off;'


