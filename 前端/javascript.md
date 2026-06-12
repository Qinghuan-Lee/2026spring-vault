
> [!resources]
> [js challenger](https://jschallenger.com)
> 可惜了 要付费



> javascript 是什么 语法是什么 怎么用

JavaScript 是一种广泛使用的编程语言，最初为网页开发而生，现在也用于服务器端、移动应用、桌面应用等领域。

# 它是什么

JavaScript 是一种动态类型、解释执行的脚本语言。它和 HTML、CSS 一起构成了现代网页的三大核心技术：HTML 负责结构，CSS 负责样式，JavaScript 负责交互和逻辑。

# 基本语法

**变量声明**有三种方式：

javascript

```javascript
let name = "Alice";      // 可重新赋值
const age = 25;           // 不可重新赋值（常量）
var old = "旧写法";       // 早期写法，现在少用
```

**数据类型**包括：字符串 `"hello"`、数字 `42`、布尔值 `true/false`、数组 `[1, 2, 3]`、对象 `{ key: "value" }`、`null` 和 `undefined`。

**条件判断：**

javascript

```javascript
if (age >= 18) {
  console.log("成年人");
} else {
  console.log("未成年");
}
```

**循环：**

javascript

```javascript
for (let i = 0; i < 5; i++) {
  console.log(i);
}
```

**函数：**

javascript

```javascript
// 普通函数
function greet(name) {
  return "你好，" + name;
}

// 箭头函数（更简洁的写法）
const greet = (name) => "你好，" + name;
```

**对象和数组：**

javascript

```javascript
const person = { name: "小明", age: 20 };
console.log(person.name); // "小明"

const fruits = ["苹果", "香蕉", "橙子"];
console.log(fruits[0]);   // "苹果"
```

# 怎么用

最简单的方式是在浏览器里直接用。打开任意浏览器，按 `F12` 打开开发者工具，在 Console 面板输入代码就能运行。

也可以写在 HTML 文件里：

html

```html
<html>
<body>
  <button onclick="sayHi()">点我</button>
  <script>
    function sayHi() {
      alert("你好！");
    }
  </script>
</body>
</html>
```

如果想在服务器端运行，可以安装 Node.js，然后在终端执行 `node 文件名.js`。

