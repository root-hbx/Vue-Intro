# Vue-Tutorial

> Vue-Tutorial is a repo containing basic examples and annotation about [Vue.js](https://cn.vuejs.org/)

## How to Start?

### 安装Node.js

[Node.js Installation](https://nodejs.org/zh-cn/download/package-manager)

```sh
...
Example configuration has been installed to:
  /opt/homebrew/opt/tmux/share/tmux
```

### 初始化仓库


确保你安装了最新版本的 [Node.js](https://nodejs.org/)，并且你的当前工作目录正是打算创建项目的目录。在命令行中运行以下命令：

```sh
npm create vue@latest
```

这个仓库内很显然`vue@latest`就是`bxhuVue`

这一指令将会安装并执行 [create-vue](https://github.com/vuejs/create-vue)，它是 Vue 官方的项目脚手架工具

### 服务器启动


在项目被创建后，通过以下步骤安装依赖并启动开发服务器：

```sh
cd <your-project-name, namely 'bxhuVue' here> 
npm install 
npm run dev
```

现在应该已经运行起来了你的第一个 Vue 项目

这是现在的文件架构:

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


## Basic Examples and GUIs

[ref-example](https://vuejs.org/examples/#hello-world)

- Basic
  - Hello World: 1-test.vue
  - Handling User Input: 2-test.vue
  - Attribute Bindings: 3-test.vue
  - Conditionals and Loops: 4-test.vue
  - Form Bindings: 5-test.vue
  - Simple Component: 6-test.vue && 6-TodoItem.vue
- GUIs
  - Counter: 7-test.vue
  - Temperature Converter: 8-test.vue
  - Flight Booker: 9-test.vue
  - Timer: 10-test.vue
  - CRUD
  - Circle Drawer
  - Cells

__How to run these scripts?__

Starters should modify the corresponding context in `$HOME/src/App.vue` in match with the script you wanna test.

For example, when you need to run `1-test.vue`, You should de-comment this part in `$HOME/src/App.vue` and make other texts in comment.

```js

<template>
  <div id="app">
    <CorrespondingSignal />
  </div>
</template>

<script setup>
import CorrespondingSignal from './components/1-test.vue'
</script>

<!-- <template>
  <div id="app">
    <CorrespondingSignal />
  </div>
</template>

<script setup>
import CorrespondingSignal from './components/2-test.vue'
</script> -->
```

然后，我们就可以在`$HOME`下运行了

```sh
cd <your-project-name, namely 'bxhuVue' here> 
npm run dev
```

它会显示这样的界面，随后点击localhost即可访问

```sh
VITE v5.3.3  ready in 139 ms

➜  Local:   http://localhost:5173/
➜  Network: use --host to expose
➜  press h + enter to show help
```

