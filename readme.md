## Prerequirments
- git
- docker v 19+
- docker-compose v 1.25+

## Instalation
1. Clone project with submodules
```
git clone --recurse-submodules https://github.com/prisma-cms/docker my-project-name
cd my-project-name
```
2. Copy and edit environments file
```
cp .env.sample .env
```
3. Copy and edit web-server config file
```
cp caddy/Caddyfile.sample caddy/Caddyfile
```
4. Copy and edit coturn config file
```
cp coturn/turnserver.conf.sample coturn/turnserver.conf
```

## Start dev

### First start

```
docker-compose -f docker-compose.yml -f docker-compose.dev.yml up --build -d mysql
```

Check this containers been started
```
docker-compose ps mysql
```

Start proxy server
```
docker-compose -f docker-compose.yml -f docker-compose.dev.yml up --build -d proxy
```


### WebRTC services for videochats

```
docker-compose -f docker-compose.yml -f docker-compose.dev.yml up --build -d rtcmultyconnection coturn
```

### Additional services

Start PhpMyAdmin
```
docker-compose -f docker-compose.yml -f docker-compose.dev.yml up --build -d pma
```
After try open http://localhost:2017


## Start prod
```
docker-compose -f docker-compose.yml -f docker-compose.prod.yml up --build -d
```

## Stop all containers
```
# In project's folder
docker-compose stop
```

## Remove all containers
```
# In project's folder
docker-compose down
```