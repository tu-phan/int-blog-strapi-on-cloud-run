FROM nginx:stable-alpine

COPY ./compose/production/my-project-nginx/nginx.fe.conf /etc/nginx/conf.d/default.conf
COPY ./my-project/build /var/www/public/html