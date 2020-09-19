# Crear volumenes 
```
docker volume create kong-vol
```
# Copiar el archivo **kong.yml** al directorio
```
docker inspect kong-vol
```
# Iniciar el servicio de kong

cd ./Kong
docker-compose up 
