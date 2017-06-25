# ECoWare + Rubis on Docker

#### Setup DB
```
cat rubis-mysql/tempb.part* > rubis-mysql/backup.tar
rm rubis-mysql/tempb.part*
docker run --name rubis-data polimi/rubis-data
docker run --name fill-db --volumes-from rubis-data -v $(pwd)/rubis-mysql:/backup polimi/rubis-mysql tar xvf /backup/backup.tar
docker rm -f fill-db
```

#### Start Rabbit
```
docker run -d -p 5672:5672 --name rabbitmq polimi/ecoware-rabbitmq rabbitmq-server
```

#### Start DB
```
docker run -d -P --volumes-from rubis-data --name rubis-db1 polimi/rubis-mysql mysqld
```

#### Start JBoss
```
docker run -d -p 8080:8080 --link rubis-db1:db --link rabbitmq:rabbitmq --name rubis-jboss1 polimi/rubis-jboss
```
