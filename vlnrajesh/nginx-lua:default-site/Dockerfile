#Base Image
FROM vlnrajesh/nginx-lua:1.11.10
ADD test_site/html /usr/share/nginx/html
ADD test_site/conf.d /etc/nginx/conf.d
ENTRYPOINT ["nginx", "-g", "daemon off;"]