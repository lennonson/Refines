# 常见命令

| **命令**       | **说明**                         |
| :------------- | :------------------------------- |
| docker pull    | 拉取镜像                         |
| docker push    | 推送镜像到DockerRegistry         |
| docker images  | 查看本地镜像                     |
| docker rmi     | 删除本地镜像                     |
| `docker run`   | `创建并运行容器（不能重复创建）` |
| docker stop    | 停止指定容器                     |
| docker start   | 启动指定容器                     |
| docker restart | 重新启动容器                     |
| docker rm      | 删除指定容器                     |
| `docker ps`    | `查看容器`                       |
| docker logs    | 查看容器运行日志                 |
| docker exec    | 进入容器                         |
| docker save    | 保存镜像到本地压缩文件           |
| docker load    | 加载本地压缩文件到镜像           |
| docker inspect | 查看容器详细信息                 |

![a63d0b60-240e-4246-8897-f4b0c249380e](D:\refines\refines\a63d0b60-240e-4246-8897-f4b0c249380e.png)

- 实现虚拟机开机自启docker

  ```bash
  # Docker开机自启
  systemctl enable docker
  
  # Docker容器开机自启
  docker update --restart=always [容器名/容器id]
  ```

- e.g 拉取nginx

  ```bash
  # 第1步，去DockerHub查看nginx镜像仓库及相关信息
  
  # 第2步，拉取Nginx镜像 (比较耗时)
  docker pull nginx:1.20.2
  
  # 第3步，查看镜像
  docker images
  
  # 第4步，创建并允许Nginx容器
  docker run -d --name nginx -p 80:80 nginx
  
  # 第5步，查看运行中容器
  docker ps
  
  # 也可以加格式化方式访问，格式会更加清爽
  docker ps --format "table {{.ID}}\t{{.Image}}\t{{.Ports}}\t{{.Status}}\t{{.Names}}"
  
  # 第6步，访问网页，地址：http://虚拟机地址
  
  # 第7步，停止容器
  docker stop nginx
  
  # 第8步，查看所有容器
  docker ps -a --format "table {{.ID}}\t{{.Image}}\t{{.Ports}}\t{{.Status}}\t{{.Names}}"
  
  # 第9步，再次启动nginx容器
  docker start nginx
  
  # 第10步，再次查看容器
  docker ps --format "table {{.ID}}\t{{.Image}}\t{{.Ports}}\t{{.Status}}\t{{.Names}}"
  
  # 第11步，查看容器详细信息
  docker inspect nginx
  
  # 第12步，进入容器,查看容器内目录
  docker exec -it nginx bash
  
  # 或者，可以进入MySQL
  docker exec -it mysql mysql -uroot -p
  
  # 第13步，删除容器
  docker rm nginx
  
  # 发现无法删除，因为容器运行中，强制删除容器
  docker rm -f nginx
  ```

# 常见参数

1. `-d`: 是让容器在后台运行
2. `--name`: 起名字
3. `-p`(port): 设置端口映射
4. `-e`(environment): 设置环境变量
5. `mysql:8`: 指定运行的镜像的名字，版本 

## 镜像命名规范

- 镜像名称
  1. `[repository]`镜像名
  2. `[tag]`镜像的版本
     在没有指定tag时，默认是latest，代表最新版本的镜像

# 数据卷

**数据卷（volume）**是一个虚拟目录，是**`容器内目录`**与**`宿主机目录`**之间`映射的桥梁`。

以Nginx为例，我们知道Nginx中有两个关键的目录：

- `html`：放置一些静态资源
- `conf`：放置配置文件

我们必须利用数据卷将两个目录与宿主机目录关联，方便我们操作。

![b67e1f6f-7bab-435a-aa05-a0f78ee5de70](D:\refines\refines\b67e1f6f-7bab-435a-aa05-a0f78ee5de70.png)

- 我们创建了两个数据卷：`conf`、`html`
- Nginx容器内部的`conf`目录和`html`目录分别与两个数据卷关联。
- 而数据卷conf和html分别指向了宿主机的
  `/var/lib/docker/volumes/conf/_data`目录和`/var/lib/docker/volumes/html/_data`目录

这样以来，容器内的`conf`和`html`目录就 与宿主机的`conf`和`html`目录关联起来，我们称为**`挂载`**。

数据卷的相关命令有：

| **命令**              | **说明**             | **文档地址**                                                 |
| :-------------------- | :------------------- | :----------------------------------------------------------- |
| docker volume create  | 创建数据卷           | [docker volume create](https://docs.docker.com/engine/reference/commandline/volume_create/) |
| docker volume ls      | 查看所有数据卷       | [docs.docker.com](https://docs.docker.com/engine/reference/commandline/volume_ls/) |
| docker volume rm      | 删除指定数据卷       | [docs.docker.com](https://docs.docker.com/engine/reference/commandline/volume_prune/) |
| docker volume inspect | 查看某个数据卷的详情 | [docs.docker.com](https://docs.docker.com/engine/reference/commandline/volume_inspect/) |
| docker volume prune   | 清除数据卷           | [docker volume prune](https://docs.docker.com/engine/reference/commandline/volume_prune/) |

> ==注意==：容器与数据卷的挂载要在`创建容器时配置`，对于创建好的容器，是不能设置数据卷的。而且**创建容器的过程中，数据卷会`自动创建`**。

## 匿名卷

```bash
docker exec -it nginx bash
```

- 进入容器内部

```bash
docker inspect mysql
```

- 查看容器的详细信息

```json
{
  "Config": {
    // ... 略
    "Volumes": {
      "/var/lib/mysql": {}
    }
    // ... 略
  }
}
```

```json
"Mounts": [
            {
                "Type": "volume",
                "Name": "e2a02b17649554e6718f3439307b606ad551d321842b2b502cb2f681b3b7d546",
                "Source": "/var/lib/docker/volumes/e2a02b17649554e6718f3439307b606ad551d321842b2b502cb2f681b3b7d546/_data",
                "Destination": "/var/lib/mysql",
                "Driver": "local",
                "Mode": "",
                "RW": true,
                "Propagation": ""
            }
        ],
```

- 这个容器声明了一个本地目录，需要挂载数据卷，但是**数据卷未定义**。这就是`匿名卷`。
- Name：数据卷名称。由于定义容器未设置容器名，这里的就是匿名卷自动生成的名字，一串hash值。
- Source：宿主机目录
- Destination : 容器内的目录
- 匿名数据卷起到数据备份作用

### 挂载

```bash
docker run -d --name 容器名 -p 宿主机端口:容器端口 -v 宿主机目录或文件:容器内目录或文件 镜像名
```

注意：

- 本地目录必须以／或．/开头，如果直接以名称开头，会被识别为数据卷而非本地目录
- `-v mysql:/var/lib/mysql`会被识别为一个数据卷，数据卷叫`mysql`
- `-v ./mysql:/var/lib/mysql`会被识别为当前目录下的`mysql`目录

# 镜像和容器

​	当我们利用Docker安装应用时，Docker会自动搜索并下载应用`镜像（image）`。镜像不仅包含`应用本身`，还包含应用运行所需要的`环境`、`配置`、`系统函数库`。Docker会在运行镜像时创建一个隔离环境，称为`容器（container）`。

镜像仓库：存储和管理镜像的平台，Docker官方维护了一个公共仓库：`Docker Hub`。

![PixPin_2025-07-25_20-29-14](D:\refines\refines\PixPin_2025-07-25_20-29-14.png)

1. 客户端(`Client`)运行(`run`)docker

2. 守护进程(`docker daemon`)监听操作

3. 守护进程在镜像仓库中找到对应的镜像(`images`)

4. 将对应的镜像下载到本地

   ```bash
   docker images
   // 查看本地的所有镜像
   ```

5. 由镜像构建出一个容器(`container`)
   容器是docker在运行镜像时构建出来的一个隔离的运行环境, 容器之间互不影响
   一个镜像可以构建多个容器

## 自定义镜像

![462f27c5-1105-4dcd-aaf2-454aa59ba70f](D:\refines\refines\462f27c5-1105-4dcd-aaf2-454aa59ba70f.png)

打包步骤

1. 准备Linux运行环境（java项目并不需要完整的操作系统，仅仅是基础运行环境即可）
2. 安装并配置JDK
3. 拷贝jar包
4. 配置启动脚本

> **镜像就是一堆文件的集合**

### Dockerfile

| **指令**       | **说明**                                     |
| :------------- | :------------------------------------------- |
| **FROM**       | 指定基础镜像                                 |
| **ENV**        | 设置环境变量，可在后面指令使用               |
| **COPY**       | 拷贝本地文件到镜像的指定目录                 |
| **RUN**        | 执行Linux的shell命令，一般是安装过程的命令   |
| **EXPOSE**     | 指定容器运行时监听的端口，是给镜像使用者看的 |
| **ENTRYPOINT** | 镜像中应用的启动命令，容器运行时调用         |

`Dockerfile`就是一个文本文件，其中包含一个个的指令（Instruction），用指令来说明要执行什么操作来`构建镜像`。将来Docker可以根据Dockerfile帮我们构建镜像。

e.g

```bash
# 使用 CentOS 7 作为基础镜像
FROM centos:7

# 添加 JDK 到镜像中
COPY jdk17.tar.gz /usr/local/
RUN tar -xzf /usr/local/jdk17.tar.gz -C /usr/local/ &&  rm /usr/local/jdk17.tar.gz

# 设置环境变量
ENV JAVA_HOME=/usr/local/jdk-17.0.10
ENV PATH=$JAVA_HOME/bin:$PATH

# 创建应用目录
RUN mkdir -p /app
WORKDIR /app

# 复制应用 JAR 文件到容器
COPY app.jar app.jar

# 暴露端口
EXPOSE 8080

# 运行命令
ENTRYPOINT ["java","-Djava.security.egd=file:/dev/./urandom","-jar","/app/app.jar"]
```

构建镜像

```bash
docker build -t 镜像名 .
```

- `-t` ：是给镜像起名，格式依然是repository:tag的格式，不指定tag时，默认为latest
- `.`  ：是指定Dockerfile所在目录，如果就在当前目录，则指定为"."

# 网络

- 默认情况下，所有容器都是以bridge方式连接到Docker的一个虚拟网桥上

加入自定义网络的容器才可以通过容器名互相访问，Docker的网络操作命令如下:

![image-20250728160757148](C:\Users\30703\AppData\Roaming\Typora\typora-user-images\image-20250728160757148.png)

# dockerCompose

DockerCompose通过一个单独的`docker-compose.yml` 模板文件（YAML格式）来定义一组相关联的应用容器，帮助
我们实现多个相互关联的Docker容器的快速部署。

- DockerCompose的命令格式：: `docker compose [OPTIONS][COMMAND]`
- ![PixPin_2025-07-29_15-29-16](D:\refines\refines\PixPin_2025-07-29_15-29-16.png)

