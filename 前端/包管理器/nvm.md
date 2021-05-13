# nvm

nvm并非包管理器，它是用于管理多个node版本的工具

在实际的开发中，可能会出现多个项目分别使用的是不同的node版本，在这种场景下，管理不同的node版本就显得尤为重要

nvm就是用于切换版本的一个工具

## 下载和安装

最新版下载地址：https://github.com/coreybutler/nvm-windows/releases

下载nvm-setup.zip后，直接安装

## 使用nvm

nvm提供了CLI工具，用于管理node版本

在终端中输入nvm，以查看各种可用命令

> 为了加快下载速度，建议设置淘宝镜像
> node淘宝镜像：https://npm.taobao.org/mirrors/node/
> npm淘宝镜像：https://npm.taobao.org/mirrors/npm/

- 使用nvm安装node版本：nvm install 10.16.2 3. 

- nvm ls 查看所有版本； 

-  nvm use 10.16.2 可以自由切换版本；

window用户目前不支持n模块来管理Node版本，请到官网下载最新版本的安装包进行升级。

安装过程⼀路next即可，如果原来有node也会⾃动检测到。

 `nvm v `检查是否安装成功。

## 配置环境

nvm 会安装不存在  node  和  npm ，默认源在国外，建议换国内源。

```scala
nvm node_mirror https://npm.taobao.org/mirrors/node/
nvm node_mirror https://npm.taobao.org/mirrors/npm/
```

或者去nvm根⽬录` C:\Users\xxx\AppData\Roaming\nvm` 下修改**setting**⽂件：

~~~shell
root: C:\Users\20928\AppData\Roaming\nvm
arch: 64
proxy: none
originalpath: .
originalversion:
node_mirror: https://npm.taobao.org/mirrors/node/
npm_mirror: https://npm.taobao.org/mirrors/npm/
~~~

**注意：**这⾥设置的是安装node和npm本身的源，并不是设置安装node包的源，可以在选择好 node后，执⾏

```shell
npm config set registry https://registry.npm.taobao.org
```

可通过 `npm config list` 查看。

## 使用

1. 查看本地安装的所有版本；有可选参数available，显示所有可下载的版本。

   ```shell
   nvm list [available]
   ```

2. 安装，命令中的版本号可⾃定义，其中latest 表示最新的稳定版 

   ```shell
   nvm install 10.14.1
   ```

3. 使⽤特定版本 

   ```shell
   nvm use 10.14.1
   ```

4. 卸载 

   ```shell
   nvm uninstall 10.14.1
   ```
