> Node.js 是让 JavaScript 能在**浏览器之外**运行的环境。

**一句话理解：**

JavaScript 本来只能在浏览器里跑（让网页动起来）。Node.js 把 JS 的运行引擎抠出来，装到了服务器/终端上，于是 JS 就能用来写后端、写命令行工具了。

```
浏览器里的 JS  →  让网页交互
Node.js 里的 JS →  写服务器、写 CLI 工具、写脚本
```

pi-mono 就是用 Node.js 运行的命令行工具。

# 安装


> 怎么装？ 装在哪？如何判断当前装没装？

## 判断当前装没装：

在终端里运行：

bash

```bash
node -v
```

如果返回版本号（如 `v20.11.0`），说明已经装了。如果提示 `command not found`，就是没装。

也可以顺便检查 npm：

bash

```bash
npm -v
```

## 装在哪
装好后可以用 `which node`（macOS/Linux）或 `where node`（Windows）查看路径。通常在 `/usr/local/bin/node`、`~/.nvm/versions/node/...` 或 `C:\Program Files\nodejs\` 这些位置，取决于你用哪种方式安装的。

## 装在哪有区别吗

17:43


装在哪主要影响两件事：**权限**和**版本管理**，日常使用差别不大。

**常见安装位置的区别：**

- **系统全局目录**（如 `C:\Program Files\nodejs\`）：官网安装包默认装这里，所有用户共享，升级需要重新下载安装包覆盖。大多数人用这种就够了。
- **nvm 管理的目录**（如 `~/.nvm/versions/...`）：装在用户目录下，不需要管理员权限，最大好处是可以同时装多个版本随时切换。适合需要在不同项目间切换 Node 版本的开发者。
- **系统包管理器**（apt/brew）：版本通常偏旧，更新不如前两种灵活。

**对你来说：**

你在 Windows 上已经装好了，大概率是官网安装包装在 `C:\Program Files\nodejs\` 下。这完全没问题，正常用就行。只有当你将来碰到"项目 A 要求 Node 18，项目 B 要求 Node 20"这种场景时，才值得折腾 nvm-windows 来管理多版本。

# 使用

怎么用

> Node.js 的用法取决于你想干什么，大致分三种场景：

## **1. 直接运行 JS 文件**

写一个 `.js` 文件，然后用 `node` 命令跑：

js

```js
// hello.js
console.log("Hello World");
```

bash

```bash
node hello.js
```

这是最基础的用法。

## **2. 交互式环境（REPL）**

终端里直接输入 `node` 回车，就进入一个可以逐行执行 JS 的环境，适合临时测试：

bash

```bash
PS C:\Users\26272> node
> 1 + 1
2
> "hello".toUpperCase()
'HELLO'
```

按 `Ctrl+C` 两次或输入 `.exit` 退出。

## **3. 做项目（最常见的用法）**

大多数人用 Node.js 是为了跑项目或搭服务，流程一般是：

bash

```bash
mkdir my-project
cd my-project
npm init -y          # 初始化项目，生成 package.json
npm install express  # 安装依赖包
```

然后写代码，比如一个最简单的 web 服务器：

js

```js
// app.js
const express = require("express");
const app = express();

app.get("/", (req, res) => {
  res.send("你好！");
});

app.listen(3000, () => {
  console.log("服务跑在 http://localhost:3000");
});
```

bash

```bash
node app.js
```

浏览器打开 `http://localhost:3000` 就能看到结果。



```
docker run -d \
--name gopherai \
-p 8080:8080 \
-p 9090:9090 \
-e LD_LIBRARY_PATH="/root/onnxruntime-linux-x64-1.22.0/lib:$LD_LIBRARY_PATH" \
-e OPENAI_API_KEY="sk-37efdfe7e78f4a94b588f50d491f69b2" \
-e OPENAI_MODEL_NAME="qwen-plus" \
-e OPENAI_BASE_URL="https://dashscope.aliyuncs.com/compatible-mode/v1" \
huanheart/gopherai-v1 \
tail -f /dev/null
```