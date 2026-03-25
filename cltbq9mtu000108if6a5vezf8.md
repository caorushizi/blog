---
title: "云存储客户端(1) 基础环境搭建"
datePublished: 2024-03-03T16:29:41.203Z
cuid: cltbq9mtu000108if6a5vezf8
slug: 1
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1709484572263/d5a67e9e-c4f3-4dfb-a550-013e3373e321.png

---

从 2020 年初到现在已经开坑了快一年了。其实我最初想做一个完全模仿百度网盘的客户端程序，那时候还是 2019 年年初的时候，最初就是想做一个客户端，用来上传静态的网站到七牛云方便一些，以下是软件的截图。

![图片](http://static.ziying.site/%E5%8D%9A%E5%AE%A2%E5%9B%BE%E7%89%87/%E6%97%A7%E7%89%88%E4%B8%BB%E9%A1%B5.png align="left")

当时也只是想做一做玩一玩，基本功能做完之后也就没有什么进度了。知道今年年初的时候才有个想法把这个客户端完善一下。下面是新坑的页面截图：

![图片](http://static.ziying.site/switch.gif align="left")

![图片](http://static.ziying.site/switch.gif align="left")

![图片](http://static.ziying.site/upload.gif align="left")

## **开坑 oss-client：基础环境搭建**

### **使用 electron-forge**

`electron-forge`是用于创建，发布和安装现代`Electron`应用程序的完整工具，[electron forge 官网](https://www.electronforge.io/)。二话不说直接上手搞。

使用官方推荐的脚手架工具和内置的模板

```shell
npx create-electron-app oss-client --template=typescript-webpack
```

初始化的过程还是很愉快的，至少我在初始化的时候没有遇到什么大坑，如果 npm 默认的源比较慢的话，推荐这个[华为云镜像](https://mirrors.huaweicloud.com/)。还有一个需要注意的是 Windows 上安装 node-gyp 出现问题的话可以看一下[这篇文章](https://simulatedgreg.gitbooks.io/electron-vue/content/en/getting_started.html#a-note-for-windows-users)，一般来说 Windows 电脑上只要安装了 visual studio 和 python2.7 的话 electron 环境是没有什么问题的。 这个框架是官方默认的 webpack + typescript 配置。如果电脑上安装了 yarn 的话 electronforge 会默认使用 yarn 来初始化项目的。下面我们默认使用 yarn 来创建开发环境。下面是初始化完成后的目录结构。

```text
│  .eslintrc.json               - eslint 配置文件
│  .gitignore                   - git 忽略的配置文件
│  package.json                 - npm 项目的配置文件
│  tsconfig.json                - typescript 配置文件
│  webpack.main.config.js       - electron 中主线程的 webpack 配置
│  webpack.plugins.js           - electronforge 配置插件列表
│  webpack.renderer.config.js   - electron 渲染进程的 webpack 配置
│  webpack.rules.js             - electronforge 配置文件
│  yarn.lock                    - yarn 版本款控制文件
└─ src                          - 源代码目录文件
index.css
index.html
index.ts
renderer.ts
```

接下来开始配置 eslint + prettier

### **eslint 和 prettier**

[eslint](https://eslint.org/)： 查找并修复 JavaScript 代码中的问题。

[prettier](https://prettier.io/)：prettier 是一个固执己见的代码格式化程序（不知道这个固执己见的怎么理解，反正我是觉得用了它之后代码漂亮了很多，和团队中的同事代码风格一致了，之前都不敢碰同事的代码 😂）

简而言之 eslint 的规则可以避免程序中的代码错误，而 prettier 可以让团队之间代码风格保持一致。二话不说直接上手。

我们使用社区中最严格的 airbnb 风格（后来很多校验规则我都手动去掉了 😂）

npmjs 官网上有两个 airbnb 的解决方案：eslint-config-airbnb 和 eslint-config-airbnb-base。eslint-config-airbnb-base 中没有对 React 的语法校验，当然我们选择 eslint-config-airbnb。

如果你的 npm 版本大于 5 可以直接使用（如果是自己用的开发环境还是建议安装一下最新版本的 node 和 npm，因为 prettier 2 版本中已经不兼容 node10 以下的版本了）

```shell
npx install-peerdeps --dev eslint-config-airbnb
```

如果你的 npm 版本小于 5 的话，在 linux/unix 中可以使用

```shell
(
 export PKG=eslint-config-airbnb;
 npm info "$PKG@latest" peerDependencies --json | command sed 's/[\{\},]//g ; s/: /@/g' | xargs npm install --save-dev "$PKG@latest"
)
```

windows 用户可以安装使用 install-peerdeps 命令行工具

```shell
npm install -g install-peerdeps
install-peerdeps --dev eslint-config-airbnb
```

详情见[eslint-config-airbnb](https://www.npmjs.com/package/eslint-config-airbnb) 这里我们执行命令的时候还是要换一下源

```shell
npx install-peerdeps --dev eslint-config-airbnb -r registry https://mirrors.huaweicloud.com/repository/npm/
```

安装完成之后需要在项目中`.eslintrc.json`中配置一下

```json
{
  "env": {
    "browser": true,
    "es6": true,
    "node": true
  },
  "extends": [
    "eslint:recommended",
    "plugin:@typescript-eslint/eslint-recommended",
    "plugin:@typescript-eslint/recommended",
    "plugin:import/errors",
    "plugin:import/warnings",
    "airbnb",
    "airbnb/hooks"
  ],
  "parser": "@typescript-eslint/parser"
}
```

然后添加 prettier

```shell
yarn add --dev --exact prettier
```

如果项目中有 gitignore 和 eslintignore 那么 prettierignore 是基于这些文件的 安装 eslint-plugin-prettier 和 eslint-config-prettier，在`.eslintrc.json`文件中继续配置

```json
{
  "env": {
    "browser": true,
    "es6": true,
    "node": true
  },
  "extends": [
    "eslint:recommended",
    "plugin:@typescript-eslint/eslint-recommended",
    "plugin:@typescript-eslint/recommended",
    "plugin:import/errors",
    "plugin:import/warnings",
    "airbnb",
    "airbnb/hooks",
    "prettier"
  ],
  "plugins": ["prettier"],
  "rules": {
    "prettier/prettier": "error"
  },
  "parser": "@typescript-eslint/parser"
}
```

请务必确保在 extends 数组中 prettier 在最后面，prettier 会把其他项配置重写。详见[eslint-plugin-prettier](https://github.com/prettier/eslint-plugin-prettier)、[eslint-config-prettier](https://github.com/prettier/eslint-config-prettier)。 接下来要配置 react，要安装 react 和 react-dom

```shell
yarn add react react-dom
yarn add @types/react @types/react-dom --dev
```

在 eslint 中 rules 配置中添加 "react/jsx-filename-extension": "off" 来关闭 jsx 对文件类型的限制 使用 normalize.css 来覆盖浏览器中的默认样式

```shell
yarn add normalize.css
```

将 src 目录中的 renderer.ts 改为 renderer.tsx，内容如下

```jsx
import React from "react";
import reactDom from "react-dom";
import "normalize.css/normalize.css";

const App = () => {
  return <div>hello react</div>;
};

reactDom.render(<App />, document.getElementById("root"));
```

将 src 文件夹下的 index.html 内容改为

```html
<!DOCTYPE html>
<html lang="zh">
  <head>
    <meta charset="UTF-8" />
    <title>Hello World!</title>
  </head>
  <body>
    <div id="root"></div>
  </body>
</html>
```

然后运行 npm start 看到 页面中显示 hello react 就证明基本环境已经搭建完毕！