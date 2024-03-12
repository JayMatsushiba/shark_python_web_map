# shark_python_web_map
Creating a flask web application to show shark ranges

Following this series: https://youtube.com/playlist?list=PL8ApLBFiTZlwpTfOGF6LGJc61IVekKa3s&si=O8PwBfG8-Iw2DMgJ 


## calls used to start up docker containers with servers 
docker network create postgresnet

docker run -d --name postgis --network=postgresnet -e POSTGRES_PASSWORD=fr24Password -e POSTGRES_DB=shark -p 5432:5432 postgis/postgis 

docker run -d -p 8080:80 --network=postgresnet -e PGADMIN_DEFAULT_EMAIL=admin@gmail.com -e PGADMIN_DEFAULT_PASSWORD=pgadmin_password dpage/pgadmin4

docker run --network=postgresnet -dt -e DATABASE_URL=postgresql://postgres:fr24Password@postgis/shark -p 7800:7800 pramsey/pg_tileserv:latest-amd64