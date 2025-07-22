# Notes Docker

Criar conteiners com docker para rodar uma aplicação web.

## 01-conversao-temperatura

1. Criar o arquivo Dockerfile
2. Construir a imagem

```bash
cd 01-conversao-temperatura/src

docker build -t heviane/conversao-temperatura:v1 -f Dockerfile .
docker image ls

docker run -d -p 8080:8080 heviane/conversao-temperatura:v1
docker container ls
```

1. Executar a aplicação no navegador
   [http://localhost:8080/](http://localhost:8080/)

2. Subir a imagem para o Docker Hub

```bash
docker push heviane/conversao-temperatura:v1
```

OBS:
- O comando **build** é executado SEMPRE na primeira vez para construir a imagem, e depois, somente se houver alterações no Dockerfile.
- Se a nomenclatura do nome da imagem estiver correta, e a imagem não existir localmente, ele busca do Docker Hub.

## Docker IA via linha de comando

```bash
docker ai
```

SE projeto for via WSL e Docker Desktop estiver instalado no Windows, execute o passo abaixo antes de executar o comando `docker ai`.sims

```bash
cd '\\wsl$\Ubuntu\home\hevi\course-devops\01-conversao-temperatura'
```
