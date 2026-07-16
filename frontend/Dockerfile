FROM nginx:1.24.0-alpine3.17-slim
RUN rm -rf /usr/share/nginx/html/* \
    && rm -f /etc/nginx/nginx.conf \
    && rm -f /etc/nginx/conf.d/default.conf \
    && mkdir -p /var/cache/nginx/client_temp \
    && chown -R nginx:nginx /var/cache/nginx \
    && chown -R nginx:nginx /var/run \
    && chown -R nginx:nginx /etc/nginx \
    && touch /var/run/nginx.pid \
    && chown nginx:nginx /var/run/nginx.pid
RUN rm -rf /usr/share/nginx/html/* \
     && rm -rf /etc/nginx/nginx.conf \
     && rm -rf /etc/nginx/conf.d/default.conf

COPY static/ /usr/share/nginx/html/
COPY nginx.conf /etc/nginx/
USER nginx
CMD ["nginx", "-g", "daemon off;"]



# FROM nginx:1.24.0
# RUN rm -rf /usr/share/nginx/html/*
# RUN rm -rf /etc/nginx/nginx.conf
# RUN rm -rf /etc/nginx/conf.d/default.conf
# COPY static/ /usr/share/nginx/html/
# COPY nginx.conf /etc/nginx/
