# IMOD docker container
1. Install docker ... 
2. Learn docker service ... 
    - 2.0 why learn docker
    - 2.1 term: docker / image / container / layer / VM / port / volume / mount / mapping / dockerhub / Dockerfile ... 
    - 2.2 learn `Dockerfile` syntax: FROM / ARG / LABEL / ENV / CMD / ENTRYPOINT / RUN / WORKDIR 
    - 2.3 build a docker image : run / build / volume / push 
    - 2.4 interactively run docker
3. Build an IMOD docker container

sudo docker build -t imod_image:base ./docker/base/     (Dockerfile所在文件夹)
sudo docker run -itd --name imod -v /media/vrlab/b23574cf-8b0d-4ffa-ac9a-30b48a7552ec/back-end/docker/imod/container:/mnt -v /tmp/.X11-unix:/tmp/.X11-unix -e DISPLAY=unix$DISPLAY imod_image:base

图形化界面显示：xhost +

进入容器：
sudo docker attach imod               (exit后容器停止)
sudo docker exec -it imod /bin/bash   (exit后容器不停止)

sudo docker ps -a
sudo docker stop [container_1 container_2 ...]
sudo docker rm [container_1 container_2 ...]
