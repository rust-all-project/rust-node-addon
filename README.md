# 使用 neon

## 介绍

自从 Node.js v10 发布之后，Node.js 推出了用于改善开发原生模块的接口，N-API（[相关链接](https://nodejs.org/api/n-api.html)），我们这里面的 neon 构建的原理就是使用了 N-API。Node.js 对 native addon(插件)，

开发侧暴露的是 ABI (application binary interface，应用二进制接口)。

目前社区中大部分的 Node.js addon 基本都使用 C/C++ 开发。C/C++ 生态非常的繁荣，基本上你想做任何事情都能找到对应的 C/C++ 库。但是 C/C++ 缺少统一的构建工具链和包管理工具，导致了开发和维护上的很多困难。而 Rust 中有现代化的管理工具 Cargo (很好很强大)。

既然使用 neon 编写原生模块这么强大，难道它就没有缺点吗？

那是肯定有的，Native code （C/C++/Rust）在一些纯计算的场景比纯 JS 快非常多，但是一旦使用 N-API 与 Node 的 JS 引擎打交道，就会有很大的性能开销(相对计算而言)。在一些简单的计算操作中，使用原生模块进行开发的话，可能速度比纯 JS 还要慢，因为在桥接的过程中产生的性能开销已经超过了本身计算的时间，结果得不偿失，所以说为什么推荐在复杂的计算场景之中使用，比如说 swc 中的对文件编译打包就是其应用场景之一，这里面的场景就已经足够复杂了。所以我们选择的时候就要看应用场景了。

## 创建

创建 neno 项目

```shell
npm init neon my-project
```

## 安装依赖

当前目录下运行 install 脚本

```sh
$ npm install
```

## Project Layout

The directory structure of this project is:

```
interface/
├── Cargo.toml
├── README.md
├── index.node
├── package.json
├── src/
|   └── lib.rs
└── target/
```

### Cargo.toml

The Cargo [manifest file](https://doc.rust-lang.org/cargo/reference/manifest.html), which informs the `cargo` command.

## 学习更多

To learn more about Neon, see the [Neon documentation](https://neon-bindings.com).

To learn more about Rust, see the [Rust documentation](https://www.rust-lang.org).

To learn more about Node, see the [Node documentation](https://nodejs.org).
