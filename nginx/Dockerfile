FROM nginx

# MAINTAINER your_email_address

COPY nginx.conf /etc/nginx/nginx.conf

WORKDIR /etc/nginx

EXPOSE 80 443

CMD ["nginx", "-g", "daemon off;"]