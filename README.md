# traefik_proxy with ssl
docker network create traefik_proxy

create a path to store your traefik config
mkdir /home/traefik
cd /home/traefik
    
docker run -d \
  -v $PWD/traefik.yml:/etc/traefik/traefik.yml \
  -v /var/run/docker.sock:/var/run/docker.sock \
  -p 80:80 \
  -p 443:443 \
  --network traefik_proxy \
  --name traefik \
  traefik:v2.10

