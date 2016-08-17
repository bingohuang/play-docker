## 第 5 章 Docker + Nginx: 快速部署静态网站

#### 第1课时：通过镜像运行Nginx
**0、准备环境：在Mac或Windows环境**
  * 需要安装 Docker Toolbox
  * docker-machine env
  * 记下机器IP：192.168.99.100 - 后面有用
  * eval $(docker-machine env)

**1、创建映射80端口的交互式容器**
  * docker pull hub.c.163.com/library/nginx:latest - 拉取镜像
  * docker images - 查看镜像
  * docker run -p 8080:80 --name nginx_web -it hub.c.163.com/library/nginx /bin/bash - 运行容器

**2、验证Nginx安装**
  * whereis nginx - 查找Nginx
  * nginx -h － 查看帮助

**3、运行Nginx**
  * nginx - 运行Nginx
  * ps aux - 查看进程
  * Ctrl+P,Ctrl+Q - 退出容器，但不停止容器

**4、验证静态网页是否正常运行**
  * docker ps
  * docker top nginx_web
  * docker port nginx_web
  * 浏览器中打开 http://192.168.99.100:8080

#### 第2课时：通过Dockerfile运行Nginx
通过Dockerfile来运行静态页面，并且是自己修改过的静态页面

1、书写Dockerfile文件

```
FROM nginx

RUN echo "Hello Nginx on Docker" > /usr/share/nginx/html/index.html

EXPOSE 443 80
CMD 'nginx'
```
2、执行Dockerfile
docker build .


-----------------------

**5、修改静态页面**
  * docker attach nginx_web
  * vi /usr/share/nginx/html/index.html

**6、安装文本编辑器vim**
  * apt-get install -y vim

**4、修改静态页面**
  * vim /usr/share/nginx/html/index.html

**5、再次运行Nginx**
  * nginx
  * ps aux

**6、容器内验证**
  * apt-get install -y curl
  * curl http://127.0.0.1:80
  * Ctrl+P,Ctrl+Q

**7、验证网站访问**
  * docker ps
  * docker port nginx_web
  * docker top nginx_web
  * curl http://127.0.0.1:port
  * 浏览器访问
    ** 宿主机的IP
    ** 容器的IP
  * docker stop nginx_web
  * docker start -i nginx_web
  * docker exec nginx_web nginx
  * docker top nginx_web
  * 分配的IP地址和端口映射都会变化
