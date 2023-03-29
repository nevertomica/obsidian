

[TOC]

## 檢視大小的指令
```
docker image ls : 預設就會顯示size 欄位
docker ps --size: 執行中的container 大小

container < image 其因為後者包含了container 
執性時後會用到的所有環境
```



## docker run 
```
docker run default mode is 
In the attached mode, Docker can start the process in the container  
and attach the console to the process's standard input, standard output,  
and standard error. 

docker run -it  -rm
-d(detached): container 運行在背景，意思是該terminal 不會被佔用
-i: 可互動
-t: 互動的時候，回覆內容比較好閱讀
-rm: 當container exit 就會自動移除

-rm 的使用場景為以下，通常將container stopped 就是在修改Dockerfile之後，需要重新build image, run container, 用不到的舊版container 自然就會刪掉

docker run -p 127.0.0.1:80:8080/tcp ubuntu bash
This binds port 8080 of the container to TCP port 80 on 127.0.0.1 of   
the host machine. You can also specify udp and sctp ports.   
The Docker User Guide explains in detail how to manipulate ports in Docker.
▾ 
https://docs.docker.com/engine/reference/commandline/run/

docker run -p CONTAINER_PORT:HOST_MACHINE_PORT
-p 只有在 
1. HOST連CONTAINER  
2. outside of container network 連進 container

#參考
https://ithelp.ithome.com.tw/articles/10299117?sc=iThelpR

run/start 之間的差異
docker run image/ docker start container
https://stackoverflow.com/questions/34782678/difference-between-running-and-starting-a-docker-container

# docker run 的拆解
# simple run command from office doc
docker run --name some-mysql -e MYSQL_ROOT_PASSWORD=my-secret-pw -d mysql:tag

#option -d: Run container in background and print container ID
啟動的log會出現在畫面上，同時這個shell變成container 的控制台，  
除非從外側stop 這個container ，不然這個shell從此被佔用

↑ 上方的指令可以快速的啟動一個mySQL container ，
轉換成如下 ↓

docker create mysql -e MYSQL_ROOT_PASSWORD=my-secret-pw
```

## docker start

```
docker start -d(default):
container 雖然啟動但不會output 訊息出來,  
你也不能給他回應

docker start -a 
-a(attched): container 會吐東西出來顯示在終端上面，
但你不能回應 

簡單來說， 要能啟動的container 能output訊息出來， 
又能input 訊息進去，要下的指令就是  
docker start -ai CONTAINER_NAME


```

## docker cp 
將檔案搬進去container 或是從中複製出，  
使用的場景是搬出container產生的log 
```
docker cp 本機端 CONTAINER_PATH 

或是

docker cp CONTAINER_PATH 本機端
```

## docker 命名
可以為container, image 命名  
再啟container的時候可以命名，指令如下
```
docker build --tag REPOSITORY:TAG .  
這個點代表當前專案

docker run IMAGE_ID or REPOSITORY or REPOSITORY:TAG \  
--name 想取的名字
```
rename your image:
`docker tag name:tag(old) name:tag(new)`

## docker push/pull
存放docker image的地方可以在雲上: docker hub/gcp  artifact registry  
或是地端 private registry

從docker hub 下載 image 的指令
`docker pull IMAGE_NAME`


image 推上 docker hub 的程序為先登入
`docker login
    - 只需要登入一次
    - 有對應的logout`
    後確認 image 名稱和docker hub 上面的repository 一致，如下範例
```
docker push nevergotta/quarkus-restr-auth-artifact-jvm:0.0.2 
# nevergotta/quarkus-restr-auth-artifact-jvm 就是docker hub 上面的 repository 的名稱
```
    
:::info
**docker pull IMAGE_NAME** or **docker run IMAGE_NAME** 
是只會抓取 `latest tag` 的 image 
:::

`docker build` 出來的 image 會有 `tag latest`  
不論 build 幾次 `tag latest` 只有一份，
另一方面 `docker tag` 產生出的 `tag latest ` 也只有一份，基於同一份 image 。
假設現在有一份 image 有兩個tag，其中一個tag是latest，那push tag latest 會同時上去 
還是只有上 latest 一份 ？ 只有一份.... 
但上面發生的情景是當出build 只有一份，但之後在new tag 同一份image 。 
如果今天在build 的環節就tag 兩份的話，那現在會發生什麼事？ 
push 一份就是一份，不會因為latest 和 0.0.7 版本是一樣，就同時幫你push 上去。
如果要push 上去兩份的話，你就必須push 兩次。



