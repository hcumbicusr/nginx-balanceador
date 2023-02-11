
# Ver redes docker
> docker network ls

# Crear red de docker
> docker network create --driver bridge youtube

# Levantar contenedores
> docker run -p 8011:80 --name server1 --rm -v "C:\Users\henry\docker\nginx\server1":/usr/share/nginx/html/ --network youtube nginx

> docker run -p 8012:80 --name server2 --rm -v "C:\Users\henry\docker\nginx\server2":/usr/share/nginx/html/ --network youtube nginx

> docker run -p 8013:80 --name server3 --rm -v "C:\Users\henry\docker\nginx\server3":/usr/share/nginx/html/ --network youtube nginx

# para saber las ips de los contenedores en la red interna
> docker inspect server1
* server1: 172.18.0.2
* server2: 172.18.0.3
* server3: 172.18.0.4

# para el balanceador
> docker run -p 8010:80 --name server0 --rm -v "C:\Users\henry\docker\nginx\nginx\default.conf":/etc/nginx/conf.d/default.conf --network youtube nginx

# para probar:
[link](http://localhost:8010) `` balanceador ``
[link](http://localhost:8010/serv2) `` siempre va al servidor2 ``
[link](http://localhost:8011) `` server1 ``
[link](http://localhost:8012) `` server2 ``
[link](http://localhost:8013) `` server3 ``