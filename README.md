# Nuxt SSR 案例

> 快速部署和体验Serverless架构下的 Nuxt.js SSR 项目

- [体验前准备](#体验前准备)
- [代码与预览](#代码与预览)
- [快速部署和体验](#快速部署和体验)
    - [在线快速体验](#在线快速体验)
    - [在本地部署体验](#在本地部署体验)
- [项目使用注意事项](#项目使用注意事项)

## 体验前准备

该应用案例，需要您开通[阿里云函数计算](https://fcnext.console.aliyun.com/) 产品；并建议您当前的账号有一下权限存在`FCDefaultRole`。

## 代码与预览

- [:octocat: 源代码](https://github.com/devsapp/start-web-framework/tree/master/web-framework/nodejs/nuxt-ssr/src)

## 快速部署和体验
### 在线快速体验

- 通过阿里云 **Serverless 应用中心**： 可以点击 [【🚀 部署】](https://fcnext.console.aliyun.com/applications/create?template=nuxt-ssr-app) ，按照引导填入参数，快速进行部署和体验。

### 在本地部署体验

1. 下载安装 Serverless Devs：`npm install @serverless-devs/s` 
    > 详细文档可以参考 [Serverless Devs 安装文档](https://github.com/Serverless-Devs/Serverless-Devs/blob/master/docs/zh/install.md)
2. 配置密钥信息：`s config add`
    > 详细文档可以参考 [阿里云密钥配置文档](https://github.com/devsapp/fc/blob/main/docs/zh/config.md)
3. 初始化项目：`s init nuxt-ssr-app -d nuxt-ssr-app`
4. 进入项目并部署：`cd nuxt-ssr-app && s deploy`

> 在本地使用该项目时，不仅可以部署，还可以进行更多的操作，例如查看日志，查看指标，进行多种模式的调试等，这些操作详情可以参考[函数计算组件命令文档](https://github.com/devsapp/fc#%E6%96%87%E6%A1%A3%E7%9B%B8%E5%85%B3) ;

## 项目使用注意事项

1. 项目Yaml中，声明了`actions`，其对应的命令为`npm install --production`，如果在使用项目时，遇到类似找不到`npm`命令的情况，请根据自身电脑关于`nodejs`与`nmp`的配置对此出进行修改，或者手动进行依赖安装，并注释掉这`actions`部分代码；
2. 目前函数计算支持的项目代码包大小为100M，如果一个完整的项目依赖包过大，可以按照以下方法进行优化和处理：
    - 将部分静态资源等，放在对象存储中，以降低代码包的体积；
    - 将 `nasConfig` 配置为 `auto`，然后基于 nas 指令将大文件（可能是训练集/依赖包）传输到 NAS 指定位置，然后配置相应的环境变量到 `s.yml` 中的函数配置中；
    - 将非 custom-container 的函数转换成 custom-container，这需要对代码进行一定的改造，并新增 dockerfile，然后创建这个函数（此方式冷启动时间相对其他 runtime 会有一点点的延长）；

-------

> - Serverless Devs 项目：https://www.github.com/serverless-devs/serverless-devs   
> - Serverless Devs 文档：https://www.github.com/serverless-devs/docs   
> - Serverless Devs 钉钉交流群：33947367    
