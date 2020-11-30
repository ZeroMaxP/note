## Base Command

### 镜像获取

> docker pull [选项] [Docker Registry 地址[:端口号]/]仓库名[:标签]

### 列出镜像

列表包含了 `仓库名`、`标签`、`镜像 ID`、`创建时间` 以及 `所占用的空间`。

> docker image ls [optional]

```sh
docker image ls ubuntu:18.04 // 包含仓库名和tag
docker image ls -f since=mongo:3.2 // 在mongo:3.2之后创建的镜像
docker image ls -f label=com.example.version=0.1 // 根据label筛选
docker image ls -q // 单独输出id
docker image ls --format "{{.ID}}: {{.Repository}}" // 利用模板输出
```



### 显示虚悬镜像

> docker image ls -f dangling=true

### 删除虚悬镜像

> docker image prune

### 删除本地镜像

> docker image rm [选项] <镜像1> [<镜像2> ...]

可以利用长短id，镜像名，镜像摘要来删除

${Untagged}$	为删除镜像名的标签，当一个镜像有多个tag时，删除一个tag镜像不会删除

${Deleted}$	删除镜像

```sh
docker image rm $(docker image ls -q redis) // 删除仓库名为redis的
docker image rm $(docker image ls -q -f before=mongo:3.2)
```

### 构建镜像

> docker commit [选项] <容器ID或容器名> [<仓库名>[:<标签>]] (不适宜使用)

```sh
$ docker commit \
    --author "Tao Wang <twang2218@gmail.com>" \
    --message "修改了默认网页" \
    webserver \
    nginx:v2
```

## Dockerfile

## FROM

> 指定基础镜像

除了选择现有镜像为基础镜像外，Docker 还存在一个特殊的镜像，名为 `scratch`。这个镜像是虚拟的概念，并不实际存在，它表示一个空白的镜像。

```dockerfile
FROM nginx
RUN echo '<h1>Hello, Docker!</h1>' > /usr/share/nginx/html/index.html
```

### RUN

- *shell* 格式：`RUN <命令>`，就像直接在命令行中输入的命令一样。刚才写的 Dockerfile 中的 `RUN` 指令就是这种格式。
- *exec* 格式：`RUN ["可执行文件", "参数1", "参数2"]`，这更像是函数调用中的格式。

每一个 `RUN` 的行为，就和刚才我们手工建立镜像的过程一样：新建立一层，在其上执行这些命令，执行结束后，`commit` 这一层的修改，构成新的镜像。

```dockerfile
FROM debian:stretch

RUN set -x; buildDeps='gcc libc6-dev make wget' \
    && apt-get update \
    && apt-get install -y $buildDeps \
    && wget -O redis.tar.gz "http://download.redis.io/releases/redis-5.0.3.tar.gz" \
    && mkdir -p /usr/src/redis \
    && tar -xzf redis.tar.gz -C /usr/src/redis --strip-components=1 \
    && make -C /usr/src/redis \
    && make -C /usr/src/redis install \
    && rm -rf /var/lib/apt/lists/* \
    && rm redis.tar.gz \
    && rm -r /usr/src/redis \
    && apt-get purge -y --auto-remove $buildDeps
# 每一层的最后需要清除不必要的软件和缓存
```

### 构建镜像

> docker build [选项] <上下文路径/URL/->

