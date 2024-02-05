# TP1 - Docker

```Dockerfile
FROM postgres:14.1-alpine

ENV POSTGRES_DB=db \
   POSTGRES_USER=usr \
   POSTGRES_PASSWORD=pwd
```

```bash
docker build -t tp1-database database
docker network create app-network
docker run -d \
    --name database \
    --network app-network \
    -e POSTGRES_PASSWORD="SecretPassword1!" \
    -v database:/var/lib/postgresql/data \
    tp1-database

docker run -d \
    --name adminer \
    --network app-network  \
    -p "8080:8080" \
    adminer:4.8.1
```



![alt text](.res/image.png)