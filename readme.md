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


## anotar

tenes el proyecto

creas docker-compose.yml

```
services:
  myapp:
    image: node:18
    expose:
      - 3000
    ports:
      - "3000:3000"
    volumes:
      - .:/app
    command: ["tail","-f","/dev/null"]
```

`docker compose up`
`docker exec -it elname bash`
`cd app`
`npm run dev`

Listo podes programar por fuera y  ver los cambios en localhost:3000

Tambien podes crear la imagen docker y correr la app pero solo para verla

```
# Usa una imagen de Node.js
FROM node:18

# Establece el directorio de trabajo en /app
WORKDIR /app

# Copia el contenido del proyecto React al contenedor
COPY . .

# Instala las dependencias
RUN npm install

# Expone el puerto 3000
EXPOSE 3000

# Inicia la aplicación React
CMD ["npm", "start"]

```

```
docker build -t my-react-app .
docker run -p 3000:3000 my-react-app

```
