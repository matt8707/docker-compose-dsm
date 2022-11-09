# docker-compose-dsm

**Synology DSM 7** path to `docker-compose/`

```bash
cd docker-compose
.  ..  docker-compose.yml  README.md  .env
```

`.env` file which contains `${VARIABLES}`

```
COMPOSE_HTTP_TIMEOUT=200
PUID=1026
PGID=100
OPENVPN_USERNAME=matt87
OPENVPN_PASSWORD='longjohnson'
TRANSMISSION_RPC_USERNAME=matt
TRANSMISSION_RPC_PASSWORD=allrightthenkeepyoursecrets
MARIADB_PASSWORD='hunter2'
```

rootless docker

```bash
sudo synogroup --add docker $USER
sudo chown root:docker /var/run/docker.sock
logout
```

useful commands

```bash
docker-compose pull && \
docker-compose down && \
docker-compose up -d

#delete unused (except watchtower)
docker system prune --volumes -af --filter "label!=watchtower"

#watchtower log
docker logs -f --since 5m watchtower

#bash inside container
docker exec -it container-name bash

#list all containers
docker ps -a
```
