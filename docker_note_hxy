>第三次尝试学习docker。第四次的时候写一个实际案例。

## * Dockerfile文件 -> 生成 image文件 -> 生成 container文件 *
[参考文献](https://blog.csdn.net/itguangit/article/details/80222387)
#### 一. Docker把应用程序及其依赖打包在一个image文件里面,可以理解为一个容器的说明书. 通过这个image文件可以生成容器的实例.同一个image文件可以生成同时运行的多个实例.

**Docker 的官方仓库 https://hub.docker.com/**

- 将 image 文件从仓库抓取到本地
`$ docker image pull library/hello-world`
 - 由于Docker官方提供的文件都放在library组里面,所以他是默认组,可以省略
- 查看本地image文件
`docker image ls`
或
`docker images`

#### 二. image文件生成的实例本身也是一个文件,成为container 容器文件.也即是说,一旦容器生成,就会存在两个文件:一个image文件,一个容器文件.而且关闭容器并不会删除容器文件,只是容器停止运行而已.
> - **运行这个image文件
`docker container run hello-world`**

>- 删除image文件
`docker image rm [imageName]`
- 终止image文件
`docker container kill [container_id]`
- 删除容器
`docker container rm [container_id]`
  - 终止运行的容器文件依然会占用硬盘空间,可以使用命令删除.
- 在容器终止运行后自动删除容器文件
`docker container run --rm -p 8000:3000 -it koa-demo /bin/bash`
> - 列出本机正在运行的容器
`docker container ls`
- 列出本机所有容器，包括终止运行的容器
`docker container ls --all`

#### 三. Dockerfile是一个文本文件,用来配置image。Docker容器根据Dockerfile文件生成image二进制文件。

## 实例：制作自己的 Docker 容器

1. 先下载源代码:
```
$ git clone https://github.com/ruanyf/koa-demos.git
$ cd koa-demos
```
2. 编写 Dockerfile 文件
>首先，在项目的根目录下，新建一个文本文件.dockerignore，写入下面的内容,表示这三个路径要排除,不要打包进image文件
```
.git
node_modules
npm-debug.log
```
3. 在项目根目录下再新建一个Dockerfile文本文件,写入下面的内容:
```
FROM node:8.4
COPY . /app
WORKDIR /app
RUN npm install --registry=https://registry.npm.taobao.org
EXPOSE 3000
CMD node demos/01.js
```
> - From node:8.4 : 该image继承自官方的node image,冒号表示标签,这里表示8.4,即8.4版本的node.
  - COPY . /app :将当前目录下的所有文件都拷贝到image文件的 /app 目录.
  - WORKDIR /app : 指定接下来的工作目录为 /app .
  - RUN npm install：在/app目录下，运行npm install命令安装依赖。注意，安装后所有的依赖，都将打包进入 image 文件。
  - EXPOSE 3000 : 将容器的3000 端口暴露出来,允许外部连接这个端口.
  - CMD ： 容器启动后,自动执行node demos/01.js。可选
  - **一个Dockerfile文件可以包含多个RUN命令,但只能包含一个CMD命令**

4. 创建 image 文件
```
$ docker image build -t koa-demo .
# 或者
$ docker image build -t koa-demo:0.0.1 .
```
> - -t参数：用来指定image文件的名字,后面还可以用冒号指定标签,如果不指定,默认标签就是latest,
  - . ：表示Dockerfile文件所在的路径.
#### 制作好以后可以用一、二的操作运行容器等等。
```
$ docker container run -p 8000:3000 -it koa-demo /bin/bash
# 或者
$ docker container run -p 8000:3000 -it koa-demo:0.0.1 /bin/bash
```
> - -p : 容器的3000端口映射到本地的8000端口.
  - -it : 容器的shell会映射到当前本地的shell,你在本机窗口输入的命令会传入到容器中.
  - koa-demo:0.0.1 ：image 文件的名字（如果有标签，还需要提供标签，默认是 latest 标签）。
  - /bin/bash : 容器启动以后,容器内部第一个执行的命令.这里是启用Bash,以保证用户可以使用shell

#### 这个例子中node进程运行在Docker容器的虚拟环境里面,进程接触到的文件系统和网络接口都是虚拟的,与本机文件系统和网络接口都是隔离的,因此需要定义容器与物理机的端口映射(map).
#### 在容器的命令行下,按ctrl+c停止node进程,按ctrl+d(或者exit)退出容器.此外,也可以使用docker container kill [container-id]终止容器的运行.

#### 四、发布image文件
1. 去 hub.docker.com 或 cloud.docker.com注册一个账户
  - 用下面的命令登录。
`docker login`
为本地的 image 标注用户名和版本。
2. 为本地的 image 标注用户名和版本。
```
$ docker image tag [imageName] [username]/[repository]:[tag]
# 实例
$ docker image tag koa-demos:0.0.1 ruanyf/koa-demos:0.0.1
```
也可以不标注用户名，重新构建一下 image 文件。
```
$ docker image build -t [username]/[repository]:[tag] .
```
3. 发布 image 文件。
`$ docker image push [username]/[repository]:[tag]`
4. 登录 hub.docker.com，就可以看到已经发布的 image 文件
