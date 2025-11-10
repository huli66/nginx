#

## TODO

使用 docker-compose 启动 nginx

docker run --rm -p 443:443 -p 80:80 --name nginx -v /root/nginx/ssl:/etc/nginx/ssl -v /root/nginx/conf/conf.d:/etc/nginx/conf.d -v /root/nginx/log:/var/log/nginx -v /root/nginx/html:/usr/share/nginx/html -d nginx:latest
