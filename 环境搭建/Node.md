# nvm安装
---
- 安装环境
![macOS.png](quiver-image-url/7C05892461029F40AE0F12DAF56026CB.png =559x269)
- [GitHub/nvm](https://github.com/creationix/nvm/blob/master/README.md)

### 1. 安装与更新
Terminal输入:
```
curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.34.0/install.sh | bash
```
或者:
```
wget -qO- https://raw.githubusercontent.com/creationix/nvm/v0.34.0/install.sh | bash
```

### 2. 查看是否安装成功
Terminal输入:
```
command -v nvm
```

# Node安装
---
### 1.下载网址
- [Node.JS EN](https://nodejs.org/en/)
- [Node.JS CN](http://nodejs.cn/)
### 2.检查是否安装成功
Terminal输入:
```
node -v
npm -v
```
若查看安装路径:
```
which node
```
#使用nvm管理NodeJS版本
---
### 1.常用命令
[参考文档](http://html5book.bluej.cn/#/md/14-nodejs/nodejs本地开发环境部署/2.使用nvm管理node版本?id=mac环境)
>nvm ls  //列举出所有已经安装的node版本
>nvm install 7.7.3      //安装7.7.3版本的nodejs
>nvm use 7.7.3           //切换nodejs版本为7.7.3
>nvm uninstall 7.7.3        //卸载7.7.3版本的nodejs
### 2.示例
```
liumorandeMacBook-Pro:bj_pro03 moran$ node -v
v6.11.1
liumorandeMacBook-Pro:bj_pro03 moran$ nvm install 8.11.3
Downloading and installing node v8.11.3...
Downloading https://nodejs.org/dist/v8.11.3/node-v8.11.3-darwin-x64.tar.xz...
######################################################################## 100.0%
Computing checksum with shasum -a 256
Checksums matched!
Now using node v8.11.3 (npm v5.6.0)
liumorandeMacBook-Pro:bj_pro03 moran$ node -v
v8.11.3
liumorandeMacBook-Pro:bj_pro03 moran$ nvm use 6
Now using node v6.11.1 (npm v3.10.10)
liumorandeMacBook-Pro:bj_pro03 moran$ nvm use 8
Now using node v8.11.3 (npm v5.6.0)
liumorandeMacBook-Pro:bj_pro03 moran$
```

