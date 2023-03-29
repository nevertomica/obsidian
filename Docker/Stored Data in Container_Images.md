
## 資料類型

- Application(Code + Environment)
    - Read only, if yout want to change, then you must be rebuild the image
- Temporary App Data
    - Read and Write, the data of running container fetched/produced
- Permanent App Data
    - Read and write, the same source like temporary app data, but we wanna to persistent,
ant this kind of data is stored by containers & volumes


## the command to use volume to store data
在host machine 上面會有一個 file 可以和 container 的另一個做同步，特別的是如果container 被刪除，container外面的資料夾是會被保存下來的，而這個本機上面的資料夾被將為
`Volumes`

為什麼前後會有 cross-errors

Dockerfile 裡頭必須指定 `VOLUME["container_folder_name"]` 
啟動docker run -v `OUTSIDE_VOLUME_NAME: inside_folder_path `

:::info
docker run --rm 會刪除匿名volumes(沒有下達 -v option)

但如果本來就沒有--rm, 那就不會自動刪除匿名volume 
可透過
```
docker volume rm VOLUME_NAME
or
docker volume prone
#Remove all unused local volumes
```
:::

---

## mount 傳遞資料
