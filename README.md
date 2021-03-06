# Introduccion a Docker 

Luis E Garcia
2021-07-07




- Introduccion

Presentacion basica de fundamentos tecnicos y vision general de conceptos relevantes y su relacion con un ambiente Cloud tipo OpenShift.

- Links: 
    - [Docker en Wikipeda](https://en.wikipedia.org/wiki/Docker_(software) )

</br>

## demo 01: Instalacion de docker en CentOS 7

```bash
yum update
yum -y install docker


systemctl start docker
systemctl status docker
systemctl enable docker
```




## demo 02: Servidor Jupyter

Ejecucion con auto eliminacion al terminar el proceso

```bash
docker run --rm --name jupyterdock -p 8888:8888 jupyter/scipy-notebook

```
Ejemplo de uso de volume, para preservacion de documentos jupyter 

```bash
# create directory for preserving folders / notebooks
mkdir -p /opt/jupyter_data
chmod 777 /opt/jupyter_data

docker run --rm --name jupyterdock -v /opt/jupyter_data:/home/jovyan -p 8888:8888 jupyter/scipy-notebook

```


```bash
cd /opt/jupter_data
ls -la
```


## demo 03: Dockerfile 

Download code from git
```bash
cd $HOME
git clone https://github.com/leqgarcia/docker_demo.git
cd docker_demo/demo03
```

Build the image and tag it
```bash
vim Dockerfile
docker build -t getting-started .
```

Clean up
```bash
cd
rm -Rf $HOME/docker_demo
```



## demo 04: Docker compose
Version HTTP
```bash

cd $HOME/docker_demo/demo04

docker-compose up



```




## demo 05: Portainer
Version HTTP
```bash

docker run -td --privileged -p 9000:9000 -p 8000:8000 \
--name portainer --restart always \
-v /certs/privkey1.pem:/certs/privkey1.pem \
-v portainer_data:/data \
portainer/portainer-ce 

```

Version con certificados para HTTPS
```bash

docker run -td --privileged -p 9000:9000 -p 8000:8000 \
--name portainer --restart always \
-v /var/run/docker.sock:/var/run/docker.sock \
-v /certs/fullchain1.pem:/certs/fullchain1.pem \
-v /certs/privkey1.pem:/certs/privkey1.pem \
-v portainer_data:/data \
portainer/portainer-ce \
    --ssl \
    --sslcert /certs/fullchain1.pem \
    --sslkey /certs/privkey1.pem

```




## demo 06: Preparations for deploying Postgres via Portainer
```bash
# create directory for data persistence
mkdir -p /opt/pgdata       
chmod -R 777 /opt/pgdata

```

- demo06: Googleando apps contenerizados: pgAdmin






