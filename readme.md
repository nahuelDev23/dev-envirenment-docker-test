## Como programar dentro del contenedor y ver los cambios reflejados

`docker ps`

`docker exec -it gotest-myapp-1 bash`


`cd src/`

`go mod init github.com/nahueldev23/go-docker-app`

Ahora podes crear archivos en tu proyecto local y se reflejara en el docker en go 
en ambas direcciones.
