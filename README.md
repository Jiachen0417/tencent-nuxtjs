[![Serverless Nuxtjs Tencent Cloud](https://img.serverlesscloud.cn/2020310/1583829094342-nuxt.js%20_%E9%95%BF.png)](http://serverless.com)

# 腾讯云 Nuxt.js Serverless Component

简体中文 | [English](https://github.com/serverless-components/tencent-nuxtjs/blob/v2/README.en.md)

## 简介

腾讯云 [Nuxt.js](https://github.com/nuxt/nuxt.js) Serverless Component。

## 目录

0. [准备](#0-准备)
1. [安装](#1-安装)
1. [配置](#2-配置)
1. [部署](#3-部署)
1. [移除](#4-移除)

### 0. 准备

#### 初始化 Nuxt.js 项目

```bash
$ mkdir serverless-nuxtjs && cd serverless-nuxtjs
$ npx create-nuxt-app src
```

### 1. 安装

通过 npm 全局安装 [serverless cli](https://github.com/serverless/serverless)

```bash
$ npm install -g serverless
```

### 2. 配置

在项目根目录创建 `serverless.yml` 文件，在其中进行如下配置

```bash
$ touch serverless.yml
```

```yml
# serverless.yml
component: nuxtjs
name: nuxtjsDemo
org: orgDemo
app: appDemo
stage: dev

inputs:
  src:
    src: ./src
    exclude:
      - .env
  region: ap-guangzhou
  runtime: Nodejs10.15
  apigatewayConf:
    protocols:
      - http
      - https
    environment: release
```

- [更多配置](https://github.com/serverless-components/tencent-nuxtjs/tree/v2/docs/configure.md)

### 3. 部署

#### 3.1 构建静态资源

```bash
# 进入 nuxt 项目目录 src
$ cd src && npm run build
```

#### 3.2 部署到云端

如您的账号未 [登陆](https://cloud.tencent.com/login) 或 [注册](https://cloud.tencent.com/register) 腾讯云，您可以直接通过 `微信` 扫描命令行中的二维码进行授权登陆和注册。

```bash
# 进入项目根目录 serverless-nuxtjs
$ sls deploy
```

> 注意: `sls` 是 `serverless` 命令的简写。

### 4. 移除

通过以下命令移除部署的 Nuxjs 服务，包括云函数和 API 网关。

```bash
# 进入项目根目录 serverless-nuxtjs
$ sls remove
```

### 账号配置（可选）

当前默认支持 CLI 扫描二维码登录，如您希望配置持久的环境变量/秘钥信息，也可以本地创建 `.env` 文件

```bash
$ touch .env # 腾讯云的配置信息
```

在 `.env` 文件中配置腾讯云的 SecretId 和 SecretKey 信息并保存

如果没有腾讯云账号，可以在此 [注册新账号](https://cloud.tencent.com/register)。

如果已有腾讯云账号，可以在 [API 密钥管理](https://console.cloud.tencent.com/cam/capi) 中获取 `SecretId` 和`SecretKey`.

```text
# .env
TENCENT_SECRET_ID=123
TENCENT_SECRET_KEY=123
```

### 更多组件

可以在 [Serverless Components](https://github.com/serverless/components) repo 中查询更多组件的信息。

### FAQ

1. [为什么不需要入口文件了？](https://github.com/serverless-components/tencent-nuxtjs/issues/1)
