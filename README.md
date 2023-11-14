# DockerImage
basic docker images for creating Pods, services in kubernate
```bash
  17 docker build . -t nginx
  26 docker push nginxproject.azurecr.io/nginx
  27 docker tag nginx:latest nginxproject.azurecr.io/nginx:v1
  28 docker push nginxproject.azurecr.io/nginx:v1

```