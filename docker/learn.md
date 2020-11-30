### 镜像获取

> docker pull [选项] [Docker Registry 地址[:端口号]/]仓库名[:标签]

### 列出镜像

列表包含了 `仓库名`、`标签`、`镜像 ID`、`创建时间` 以及 `所占用的空间`。

> docker image ls [optional]

```
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

```dockerfile
docker image rm $(docker image ls -q redis) // 删除仓库名为redis的
docker image rm $(docker image ls -q -f before=mongo:3.2)
```

