# Orders Service Example

Este proyecto es un ejemplo de un servicio de pedidos utilizando java y Docker.

## Direcciones Ip de los contenedores que tienen los demas servicios (son consumidos por este)

- **Payments Service**: `172.17.0.2:8080`
- **Shipping Service**: `172.17.0.4:8080`
- **Products Service**: `172.17.0.3:8080`

## Construcción y ejecución del contenedor


### Construir imagen
```
docker build -t orders-service-example:1 .
```
### Crear contenedor
```
docker run -d -p 8084:8080 --name orders-service-example-container --env "APP_ARGS=http://172.17.0.2:8080 http://172.17.0.4:8080 http://172.17.0.3:8080" orders-service-example:1
```


### Obtener Ip del contenedor
```
docker inspect orders-service-example
```
=> IPAddress": "172.17.0.5"


### Verificacion de app en POSTMAN
- Request tipe: POST
- URL: http://localhost:8084/orders
- Body (raw-JSON):  

    [
        "123", "321", "111"
    ]


### Comando para verificar que todos los contenedores esten en la misma red
```
docker network inspect bridge
```


# ==> De aqui para abajo falta editar


# Empaquetado y deploy de la app

Crear Dockerfiles para cada proyecto.
    En el Dockerfile hago etapas de build y ejecucion

Construir y subir las imágenes a Amazon ECR. (esto supongo que es con githubactions)


Crear un cluster de ECS.
Crear una definición de tarea en ECS (una por cada aplicacion). 
Crear servicios en el cluster ECS (un servicio por cada app (cada servicio podria correr mas de un conteiner para hacer balanceo)).
    Configurar Load Balancer.


voy a github actions y configuro el CI/CD


cluster name
service name
setear credenciales de aws