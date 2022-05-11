### oh-my-docker(win10)
*注意：* 使用cmd 执行如下命令

+ 下载image

```
docker pull frankfang128/oh-my-docker:latest
```
+ 运行image，得到容器
```
// 获取镜像id
docker image ls
// 运行镜像
docker run -dit [镜像id前5位]
```
+ 进入容器
```
// 获取容器id
docker container ls
docker exec -it [容器id前5位] [命令行名称]
docker exec -it 40dcc zsh
```
+ 退出容器
```
// 方式一
exit
// 方式二，仅限于无输入内容时有效
ctrl + D
```
#### 连接数据库

例如：连接MYSQL

1. 创建network
    ```
     docker network create network-1
    ```
    
2. 启动mysql server，连入network的网络名称（network-1）
	```
    // google docker hub mysql image`
    docker run --name [容器名称] -e MYSQL_ROOT_PASSWORD=[密码] --network=[network 名称] -d mysql:[tag]
    docker run --name mysql-1 -e MYSQL_ROOT_PASSWORD=123456 --network=network-1 -d mysql:5.7.35
   ```
   
3. 让oh-my-docker 连入network的网络名称（network-1）

    ![container-1](C:\Users\Admin\Desktop\container-1.png)

    ![image-20220504194826927](C:\Users\Admin\AppData\Roaming\Typora\typora-user-images\image-20220504194826927.png)

```
// 进入oh-my-docker， 连接创建的mysql数据库
mysql -u root -h [数据库名称] -p
mysql -u root -h mysql-1 -p
```

