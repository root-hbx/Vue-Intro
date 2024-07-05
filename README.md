# Vue-Tutorial

> Vue-Tutorial is a repo containing basic examples and annotation about [Vue.js](https://cn.vuejs.org/)

## How to Start?

### Node.js Installation

[Node.js Installation](https://nodejs.org/zh-cn/download/package-manager)

```sh
...
Example configuration has been installed to:
  /opt/homebrew/opt/tmux/share/tmux
```

### Repository Initialization

Ensure that you have installed the latest version of [Node.js](https://nodejs.org/) and that your current working directory is the intended directory for project creation. 

Execute the following command in the command line:

```sh
npm create vue@latest
```

Obviously, `vue@latest` is `bxhuVue` here.

This command will install and execute [create-vue](https://github.com/vuejs/create-vue), which is the official project scaffolding tool provided by Vue.

### 服务器启动

After project creation, proceed with the following steps to install dependencies and start the development server.

```sh
cd <your-project-name, namely 'bxhuVue' here> 
npm install 
npm run dev
```

Now your first Vue project should be up and running.

Here is the current file structure:

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

The recommended IDE configuration is [Visual Studio Code](https://code.visualstudio.com/) with the [Vue - Official Extension](https://marketplace.visualstudio.com/items?itemName=Vue.volar).

If using a different editor, refer to the [IDE Support section](https://cn.vuejs.org/guide/scaling-up/tooling.html#ide-support).


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

Then we can run in `$HOME`

```sh
cd <your-project-name, namely 'bxhuVue' here> 
npm run dev
```

A page will be shown like this, and you can visit the corresponding website by clicking localhost_link

```sh
VITE v5.3.3  ready in 139 ms

➜  Local:   http://localhost:5173/
➜  Network: use --host to expose
➜  press h + enter to show help
```
