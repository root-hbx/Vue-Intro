# Vue-Tutorial

> Vue-Tutorial is a repo containing basic examples and annotation about [Vue.js](https://cn.vuejs.org/)

## How to Start?

__安装Node.js__

[Node.js Installation](https://nodejs.org/zh-cn/download/package-manager)

```sh
...
Example configuration has been installed to:
  /opt/homebrew/opt/tmux/share/tmux
```


__初始化仓库__

确保你安装了最新版本的 [Node.js](https://nodejs.org/)，并且你的当前工作目录正是打算创建项目的目录。在命令行中运行以下命令：

```sh
npm create vue@latest
```

这个仓库内很显然`vue@latest`就是`bxhuVue`

这一指令将会安装并执行 [create-vue](https://github.com/vuejs/create-vue)，它是 Vue 官方的项目脚手架工具


__服务器启动__

在项目被创建后，通过以下步骤安装依赖并启动开发服务器：

```sh
cd <your-project-name, namely 'bxhuVue' here> 
npm install 
npm run dev
```

你现在应该已经运行起来了你的第一个 Vue 项目

这是现在的文件架构

```sh
❯ tree -L 2
.
└── bxhuVue
    ├── README.md
    ├── dist
    ├── index.html
    ├── jsconfig.json
    ├── node_modules
    ├── package-lock.json
    ├── package.json
    ├── public
    ├── src
    └── vite.config.js

6 directories, 6 files
```

推荐的 IDE 配置是 [Visual Studio Code](https://code.visualstudio.com/) + [Vue - Official 扩展](https://marketplace.visualstudio.com/items?itemName=Vue.volar)。如果使用其他编辑器，参考 [IDE 支持章节](https://cn.vuejs.org/guide/scaling-up/tooling.html#ide-support)
