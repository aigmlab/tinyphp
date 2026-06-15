# TinyPHP Framework for PHP

## 中文

### 简介

tinyphp v2.0.0 — 面向全栈 PHP 工程师的高性能 MVC 框架。

基于 [aigm/tinyphp-framework](https://github.com/aigmlab/tinyphp-framework) v2.0.0。

```
经过日 PV 十亿级别生产环境检验;
应用于高并发高性能的生产环境;
支持分布式的 RPC 微服务处理;
适用于 Web/Console/RPC 等运行环境，包括单一命令行文件打包，多任务的服务端守护进程等。
```

### 快速开始

```shell
composer create-project aigm/tinyphp

# console 运行
php public/index.php

# 编译单文件
php public/index.php --build

# 服务端守护进程
php public/index.php -d          # 开启
php public/index.php --daemon=stop  # 关闭

# 配置文件
application/config/profile.php
```

### 核心组件

#### aigm/tinyphp-framework v2.0
框架地址: [https://github.com/aigmlab/tinyphp-framework](https://github.com/aigmlab/tinyphp-framework)

#### aigm/tinyphp-docs
中文文档: 使用手册、标准库。
项目地址: [https://github.com/aigmlab/tinyphp-docs](https://github.com/aigmlab/tinyphp-docs)

#### aigm/tinyphp-ui
前端 UI 组件库: webpack5 + bootstrap5 + jquery...
项目地址: [https://github.com/aigmlab/tinyphp-ui](https://github.com/aigmlab/tinyphp-ui)

#### lnmp-utils
Linux (CentOS 7 X64) + OpenResty (Nginx) + MySQL + PHP + Redis 一键安装包。
项目地址: [https://github.com/aigmlab/lnmp-utils](https://github.com/aigmlab/lnmp-utils)

### 快速构建运行环境

#### CentOS X64 7.4+ (生产环境)

依赖于 lnmp-utils:
> [https://github.com/aigmlab/lnmp-utils](https://github.com/aigmlab/lnmp-utils)

```shell
git clone https://github.com/aigmlab/lnmp-utils.git
cd ./lnmp-utils
./install.sh -m tinyphp
```

#### Docker (开发环境)

```shell
workspace=/data/workspace/
docker pull centos:7
docker run -d -p 80:80 -p 3306:3306 -p 8080:8080 -p 8989:8989 -p 10022:22 \
  -v $workspace:/data/web \
  --name="tinyphp" --hostname="tinyphp" --restart=always \
  -w /data/workspace/ centos:7 /sbin/init

# port 8080 用于 aigm/tinyphp-ui 调试 (npm run dev)
# port 8989 用于 aigm/tinyphp-ui 打包详情查看 (npm run build)

docker exec -it tinyphp /bin/bash
git clone https://github.com/aigmlab/lnmp-utils.git
cd ./lnmp-utils && ./install.sh
cd /data/web/aigm/tinyphp
php public/index.php
```

### 中文文档

- [Demo](https://github.com/aigmlab/tinyphp)
- [中文文档](https://github.com/aigmlab/tinyphp-docs)
  - [语言基础规范](https://github.com/aigmlab/tinyphp-docs/tree/master/docs/coding)
  - [SQL 设计规范](https://github.com/aigmlab/tinyphp-docs/tree/master/docs/sql)
  - [团队编码规范](https://github.com/aigmlab/tinyphp-docs/tree/master/docs/team)

#### 框架使用手册
- [Index/入口文件](https://github.com/aigmlab/tinyphp-docs/blob/master/docs/manual/index-001.md)
- [Application/应用](https://github.com/aigmlab/tinyphp-docs/blob/master/docs/manual/application-002.md)
- [Properties/应用配置](https://github.com/aigmlab/tinyphp-docs/blob/master/docs/manual/profile-003.md)
  - [Debug/调试模式](https://github.com/aigmlab/tinyphp-docs/blob/master/docs/manual/debug-004.md)
  - [Bootstrap/引导程序](https://github.com/aigmlab/tinyphp-docs/blob/master/docs/manual/bootstrap-005.md)
  - [Lang/语言包](https://github.com/aigmlab/tinyphp-docs/blob/master/docs/manual/lang-006.md)
  - [Data/数据源](https://github.com/aigmlab/tinyphp-docs/blob/master/docs/manual/data-007.md)
  - [Cache/缓存](https://github.com/aigmlab/tinyphp-docs/blob/master/docs/manual/cache-008.md)
  - [Router/路由器](https://github.com/aigmlab/tinyphp-docs/blob/master/docs/manual/router-009.md)
  - [Logger/日志收集](https://github.com/aigmlab/tinyphp-docs/blob/master/docs/manual/logger-010.md)
  - [Dispatcher/派发器](https://github.com/aigmlab/tinyphp-docs/blob/master/docs/manual/dispatcher-011.md)
  - [Configuration/配置类](https://github.com/aigmlab/tinyphp-docs/blob/master/docs/manual/configuration-012.md)
  - [Builder/打包](https://github.com/aigmlab/tinyphp-docs/blob/master/docs/manual/builder-013.md)
  - [Daemon/守护进程](https://github.com/aigmlab/tinyphp-docs/blob/master/docs/manual/daemon-014.md)
  - [Filter/过滤器](https://github.com/aigmlab/tinyphp-docs/blob/master/docs/manual/filter-015.md)
  - [Plugin/插件](https://github.com/aigmlab/tinyphp-docs/blob/master/docs/manual/plugin-016.md)
- [Controller/控制器](https://github.com/aigmlab/tinyphp-docs/blob/master/docs/manual/controller-017.md)
- [Model/模型](https://github.com/aigmlab/tinyphp-docs/blob/master/docs/manual/model-018.md)
- [Viewer/视图](https://github.com/aigmlab/tinyphp-docs/blob/master/docs/manual/viewer-019.md)

#### 框架标准库参考
- [Tiny: 工具包](https://github.com/aigmlab/tinyphp-docs/blob/master/docs/manual/lib/tiny.md)
- [Tiny\Runtime: 运行时](https://github.com/aigmlab/tinyphp-docs/blob/master/docs/manual/lib/runtime.md)
- [Tiny\Build: 打包](https://github.com/aigmlab/tinyphp-docs/blob/master/docs/manual/lib/build.md)
- [Tiny\Cache: 缓存](https://github.com/aigmlab/tinyphp-docs/blob/master/docs/manual/lib/cache.md)
- [Tiny\Config: 配置](https://github.com/aigmlab/tinyphp-docs/blob/master/docs/manual/lib/config.md)
- [Tiny\Console: 命令行](https://github.com/aigmlab/tinyphp-docs/blob/master/docs/manual/lib/console.md)
- [Tiny\Data: 数据层](https://github.com/aigmlab/tinyphp-docs/blob/master/docs/manual/lib/data.md)
- [Tiny\Filter: 过滤器](https://github.com/aigmlab/tinyphp-docs/blob/master/docs/manual/lib/filter.md)
- [Tiny\Image: 图片处理](https://github.com/aigmlab/tinyphp-docs/blob/master/docs/manual/lib/image.md)
- [Tiny\Lang: 语言包](https://github.com/aigmlab/tinyphp-docs/blob/master/docs/manual/lib/lang.md)
- [Tiny\Log: 日志处理](https://github.com/aigmlab/tinyphp-docs/blob/master/docs/manual/lib/log.md)
- [Tiny\MVC: MVC](https://github.com/aigmlab/tinyphp-docs/blob/master/docs/manual/lib/mvc.md)
- [Tiny\Net: 网络](https://github.com/aigmlab/tinyphp-docs/blob/master/docs/manual/lib/net.md)
- [Tiny\String: 字符处理](https://github.com/aigmlab/tinyphp-docs/blob/master/docs/manual/lib/string.md)

---

## English

### Overview

tinyphp v2.0.0 — A high-performance MVC framework for full-stack PHP engineers.

Built on [aigm/tinyphp-framework](https://github.com/aigmlab/tinyphp-framework) v2.0.0.

```
Battle-tested at 1+ billion daily PV in production;
Designed for high-concurrency, high-performance environments;
Supports distributed RPC microservices;
Works in Web/Console/RPC runtimes, including single-file packaging and daemon processes.
```

### Quick Start

```shell
composer create-project aigm/tinyphp

# Console mode
php public/index.php

# Build single executable
php public/index.php --build

# Daemon process
php public/index.php -d              # start
php public/index.php --daemon=stop   # stop

# Configuration
application/config/profile.php
```

### Core Components

| Component | Description | Repository |
|-----------|-------------|------------|
| aigm/tinyphp-framework | Core MVC framework | [github.com/aigmlab/tinyphp-framework](https://github.com/aigmlab/tinyphp-framework) |
| aigm/tinyphp-docs | Chinese documentation | [github.com/aigmlab/tinyphp-docs](https://github.com/aigmlab/tinyphp-docs) |
| aigm/tinyphp-ui | UI component library (webpack5+bootstrap5+jquery) | [github.com/aigmlab/tinyphp-ui](https://github.com/aigmlab/tinyphp-ui) |
| lnmp-utils | LNMP one-click installer | [github.com/aigmlab/lnmp-utils](https://github.com/aigmlab/lnmp-utils) |

### Environment Setup

#### CentOS X64 7.4+ (Production)

```shell
git clone https://github.com/aigmlab/lnmp-utils.git
cd ./lnmp-utils
./install.sh -m tinyphp
```

#### Docker (Development)

```shell
workspace=/data/workspace/
docker pull centos:7
docker run -d -p 80:80 -p 3306:3306 -p 8080:8080 -p 8989:8989 -p 10022:22 \
  -v $workspace:/data/web \
  --name="tinyphp" --hostname="tinyphp" --restart=always \
  -w /data/workspace/ centos:7 /sbin/init

docker exec -it tinyphp /bin/bash
git clone https://github.com/aigmlab/lnmp-utils.git
cd ./lnmp-utils && ./install.sh
cd /data/web/aigm/tinyphp
php public/index.php
```

### Documentation

Full documentation is available at [aigm/tinyphp-docs](https://github.com/aigmlab/tinyphp-docs) (Chinese).

See the [中文文档](#中文文档) section above for the complete manual index covering:
- Coding standards, SQL design guidelines, and team conventions
- Framework manual: index, application structure, configuration, MVC, caching, routing, logging
- Standard library reference: Tiny, Runtime, Build, Cache, Config, Data, Filter, Log, MVC, Net, String
