> css 是什么 语法是什么 怎么用

CSS（Cascading Style Sheets，层叠样式表）是用来控制网页外观的语言。如果把 HTML 比作房子的结构（墙、门、窗），CSS 就是装修——决定颜色、大小、位置、动画等视觉效果。

---

# 基本语法

CSS 的核心结构非常简单：

css

```css
选择器 {
  属性: 值;
  属性: 值;
}
```

比如：

css

```css
h1 {
  color: red;
  font-size: 32px;
}
```

这段意思是：所有 `<h1>` 标签的文字变成红色、字号 32px。

---

## 三种使用方式

**1. 行内样式**（直接写在标签上）

html

```html
<p style="color: blue; font-size: 16px;">你好</p>
```

**2. 内部样式**（写在 HTML 的 `<style>` 标签里）

html

```html
<style>
  p { color: blue; }
</style>
```

**3. 外部样式表**（单独的 .css 文件，推荐方式）

html

```html
<link rel="stylesheet" href="style.css">
```

---

# 常用选择器

css

```css
/* 标签选择器 */
p { color: black; }

/* 类选择器（最常用） */
.card { background: white; }

/* ID 选择器 */
#header { height: 60px; }

/* 后代选择器 */
.card p { margin: 10px; }

/* 伪类 */
a:hover { color: red; }
```

HTML 中对应写法：`<div class="card">` 或 `<div id="header">`。

---

### 最常用的属性速查

|类别|属性|示例|
|---|---|---|
|文字|`color`, `font-size`, `font-weight`, `text-align`|`color: #333;`|
|背景|`background`, `background-color`|`background: #f0f0f0;`|
|盒模型|`width`, `height`, `margin`, `padding`, `border`|`padding: 16px;`|
|布局|`display`, `flex`, `grid`, `position`|`display: flex;`|
|圆角/阴影|`border-radius`, `box-shadow`|`border-radius: 8px;`|

---

### 一个完整小例子

html

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    body {
      font-family: sans-serif;
      background: #f5f5f5;
      display: flex;
      justify-content: center;
      padding: 40px;
    }
    .card {
      background: white;
      padding: 24px;
      border-radius: 12px;
      box-shadow: 0 2px 8px rgba(0,0,0,0.1);
      max-width: 400px;
    }
    .card h2 {
      color: #333;
      margin-top: 0;
    }
    .card p {
      color: #666;
      line-height: 1.6;
    }
  </style>
</head>
<body>
  <div class="card">
    <h2>你好 CSS</h2>
    <p>这是一个用 CSS 美化过的卡片，有圆角、阴影和居中布局。</p>
  </div>
</body>
</html>
```

---

### 学习建议

先掌握这几个核心概念就能做很多事：**盒模型**（margin/padding/border）、**Flexbox 布局**（`display: flex`）、**选择器优先级**。之后再慢慢学 Grid 布局、动画、响应式设计等进阶内容。