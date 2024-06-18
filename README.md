

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


