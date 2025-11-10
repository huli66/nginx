# 

## TODO

使用 docker-compose 启动 nginx

docker run -p 9002:80 --name nginx  -v /root/nginx/conf/conf.d:/etc/nginx/conf.d -v /root/nginx/log:/var/log/nginx -v /root/nginx/html:/usr/share/nginx/html -d nginx:latest
