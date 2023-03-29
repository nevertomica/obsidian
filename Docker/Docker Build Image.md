[[操作]]
[[Docker Usual Command]]
[[Docker Compose File]]

此次會用到的command
```
docker pull mysql # pull the image of mysql

docker image rm $(docker image ls -q) 
# command_image's option q means only image IDs

docker build --no-cache -f src/main/docker/Dockerfile.jvm -t quarkus/restr-auth-artifact-jvm .
# --no-cache: build 過一次的 image，仍舊會build 一個全新的，可以從 IMAGE_ID 看出。


docker rm -f $(docker ps -aq) # 移除所有container, -q:只顯示CONTAINER_ID
docker image rm -f $(docker image ls -q) # 移除所有image
```


## 未用 Network 連接 Container
:::warning
這裡的Dockerfile 是由Intellij 幫忙建制的，並非手動建立
:::
準備一個CRUD專案，將其包成docker image，確認 crud container 可以和 db container 在分別起的情況下協作。
crud 在包成 image 前，api 的 ip 必須從 localhost 改成本機ip，請用 `ifconfig` 確認本機 ip , 才能和 db container 做溝通。

## Container Network
- 採用 bridge network 串接 container
service, db container 透過 container network 連起來
:::info
注意: 如果已經同屬一個 network 之下，jdbc url 就能採用
CONTAINER_NAME: PORT_OF_CONTAINER 
PORT_OF_CONTAINER 就是container 內部開放服務的port號
```
quarkus:
  datasource:
    db-kind: postgresql
    username: postgres
    password: postgres
    jdbc:
      url: jdbc:postgresql://loving_austin:5432/postgres
```
:::



## 寫成compose file
```yaml=
version: '3.7'
services:
  crud:
      image: quarkus/restr-auth-artifact-jvm
      environment:
        QUARKUS_PROFILE: dev
      networks:
        - MY_SP
      ports:
        - "8080:8080"
  db:
     image: postgres:latest
     container_name: loving_austin
     networks:
       - MY_SP
     restart: always
     environment:
        POSTGRES_PASSWORD: postgres
     ports:
       - "5678:5432"
  admin:
     image: adminer
     networks:
       - MY_SP
     restart: always
     ports:
       - "8084:8080"
networks:
  MY_SP:
      external: true
```
除了container 那邊要加上 network 註冊之外， 下方還要拉一塊特別註冊。
`networks:MY_SP:external:true` 代表採用事先建立好的 container network。

另外上方compose file container 的 restart policy 可以參照下方，
restart:always 雖然寫stopped 會重啟container，但情況是 docker daemon 重啟的時候才會
，而daemon 要重啟除了docker dashbord 重啟之外，基本不會發生。
▾
https://ithelp.ithome.com.tw/articles/10267079

## 注意指令

## 參考


下方為基礎範例
https:/ithelp.ithome.com.tw/articles/10191016?sc=hot

Build Image 到底要不要用Cache
https://ithelp.ithome.com.tw/articles/10246065


