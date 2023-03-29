docker compose 是一個可以同時啟多個Container的 tool，透過事先寫好的yaml檔。

[TOC]



#### Docker Compose

What is a Docker Compose service?
Docker Compose is a tool that was developed to help define and share multi-container applications. With Compose, we can create a YAML file to define the services and with a single command, can spin everything up or tear it all down.

#### docker 基本操作指令
command docker container (abbre. docker )
docker ps: 列出所有運行中的 container 
    - a : 列出所有狀態的container 
    - q : 顯示container id 
    
docker run :從image 去啟動container
docker start: 啟動已經停掉的 container
docker stop/pause : 都是停下container，差別在於stop會清空記憶體，後者卻不會。

docker create 有哪一些的選項可參考下方
https://ithelp.ithome.com.tw/articles/10257016

參考以下移除用不的container
https://docs.docker.com/engine/reference/commandline/rm/#remove-all-stopped-containers


參考
https://www.cnblogs.com/zhengah/p/4932512.html
提供如下訊息
1. command_start:Start a stopped container
2. start_option_--attach: 启动一个容器并打印输出结果和错误
特別注意到第一點，剛剛被created 出來的container 要透過docker start 給啟動意味者container_status_created: 適於stopped的一個container



##### Build One Docker Compose Yaml

撰寫 docker compose file, 再以此啟複數個 container，
**目標**: postgreSQL, Admin UI 兩個container

:::warning
1. compose file version 是對應 docker engine release
2. docker compose file 就是集成 docker run 
::: 

**程式碼**
```yaml!
version: '2'
services:
  db:
     image: postgres:latest
     restart: always
     environment:
        POSTGRES_PASSWORD: postgres
     ports:
       - "5678:5432"
  admin:
     image: adminer
     restart: always
     ports:
       - 8080:8080
```
- 上述內容之中的`db, admin` 就是在`docker run` 時候的選項 name
- 本機的port 5678可以自訂，但container開放的固定式5432，參考docker hub postgres 的官方文件

參考 
:::spoiler
[docker daemon ](https://ithelp.ithome.com.tw/articles/10190728)

[docker restart policy](https://docs.docker.com/config/containers/start-containers-automatically/#use-a-restart-policy)

[Docker Compose File Version](https://docs.docker.com/compose/compose-file/compose-versioning/)

[docker restart policy](https://ithelp.ithome.com.tw/articles/10267079)
:::

延伸study參考
:::spoiler
[進入container 修改port](https://blog.yowko.com/change-container-port-mapping/)


:::

