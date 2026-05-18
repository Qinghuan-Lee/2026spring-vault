npm 是 **Node Package Manager**

JavaScript/TypeScript 生态的包管理器，相当于 Python 的 pip，或者 Rust 的 cargo。

**它主要做三件事：**

**1. 安装别人写的代码包**

bash

```bash
npm install react        # 安装 react 这个库到当前项目
npm install -g pi        # -g 表示全局安装，装完可以在任何地方用 pi 命令
```

**2. 管理项目依赖** 每个 JS 项目都有一个 `package.json` 文件，记录这个项目依赖哪些包、版本是多少。就像一个"购物清单"，别人拿到你的项目后运行 `npm install`，就能自动把所有依赖装好。

**3. 运行脚本**

bash

```bash
npm run build    # 构建项目
npm run test     # 跑测试
```

这些脚本也定义在 `package.json` 里。


**和 pi-mono 的关系：**

pi-mono 是用 TypeScript 写的，所以你需要先装 Node.js（npm 随 Node.js 一起安装），才能安装和运行 pi。