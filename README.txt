下载最近Jenkins镜像
docker pull jenkinsci/blueocean

使用docker run 生成容器
docker run -d \
    -u root \
    --name jenkins \
    --network host \
    -v /data/jenkins/data:/var/jenkins_home \
    -v /var/run/docker.sock:/var/run/docker.sock \
    -v /etc/localtime:/etc/localtime \
    -v /etc/timezone:/etc/timezone \
    -v "$HOME:/home" \
    jenkinsci/blueocean

使用docker-compose生成容器
下载docker-compose.yml到本地 执行命令 docker-compose up -d (确保跟docker-compose.yml在同一文件夹下)

查看初始密码
docker logs jenkins 