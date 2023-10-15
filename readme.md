## Como programar dentro del contenedor y ver los cambios reflejados

`docker ps`

`docker exec -it gotest-myapp-1 bash`


`cd src/`

`go mod init github.com/nahueldev23/go-docker-app`

Ahora podes crear archivos en tu proyecto local y se reflejara en el docker en go 
en ambas direcciones.


## Con Dockerfile

```
# Utiliza la imagen oficial de Golang como imagen base
FROM golang

# Establece el directorio de trabajo en /go/src
WORKDIR /go/src

# Copia el contenido actual del directorio del proyecto al contenedor en /go/src
COPY . .

# Ejecuta el comando "tail -f /dev/null" para mantener el contenedor en ejecución
CMD ["tail", "-f", "/dev/null"]
```



