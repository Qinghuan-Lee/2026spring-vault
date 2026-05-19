# React 介绍

React 是一个用于构建用户界面的 **JavaScript 库**。它由 Facebook 开发，现在被广泛用于构建现代化的网页应用和移动应用。

## 1. React 的核心概念

### 什么是组件（Component）？

React 使用**组件**来构建 UI。每个组件都是一个可复用的代码块，负责渲染界面的一部分。

```jsx
// 最简单的组件
function Welcome() {
  return <h1>你好，React!</h1>;
}
```

### JSX 语法

JSX 是 JavaScript 和 HTML 的混合语法，让你能在 JavaScript 中写 HTML 风格的代码。

```jsx
const name = "张三";
const element = <h1>欢迎，{name}!</h1>;
// 这会渲染成 <h1>欢迎，张三!</h1>
```

## 2. 函数式组件

```jsx
function Greeting({ name, age }) {
  return (
    <div>
      <h1>你好，{name}</h1>
      <p>年龄：{age}</p>
    </div>
  );
}

// 使用组件
<Greeting name="Alice" age={25} />
```

## 3. Props（属性）

Props 是组件接收的参数，用于传递数据。

```jsx
function Card({ title, description }) {
  return (
    <div className="card">
      <h2>{title}</h2>
      <p>{description}</p>
    </div>
  );
}

// 父组件使用子组件并传递 props
<Card 
  title="React 入门" 
  description="学习 React 基础知识"
/>
```

## 4. State（状态）- 使用 Hooks

State 是组件的内部数据，当 state 改变时，组件会重新渲染。

```jsx
import { useState } from 'react';

function Counter() {
  // useState 返回：[当前值, 更新函数]
  const [count, setCount] = useState(0);
  
  return (
    <div>
      <p>计数：{count}</p>
      <button onClick={() => setCount(count + 1)}>
        增加
      </button>
    </div>
  );
}
```

## 5. 常用 Hooks

### useState - 管理状态

```jsx
const [value, setValue] = useState("");

<input 
  value={value}
  onChange={(e) => setValue(e.target.value)}
/>
```

### useEffect - 副作用处理

```jsx
import { useEffect, useState } from 'react';

function App() {
  const [data, setData] = useState(null);
  
  // 组件挂载时执行，类似生命周期
  useEffect(() => {
    // 获取数据
    fetch('/api/data')
      .then(res => res.json())
      .then(data => setData(data));
  }, []); // 空数组表示只执行一次
  
  return <div>{data}</div>;
}
```

## 6. 条件渲染

```jsx
function LoginStatus({ isLoggedIn }) {
  if (isLoggedIn) {
    return <h1>欢迎回来！</h1>;
  }
  return <h1>请登录</h1>;
}

// 或使用三元运算符
function StatusMessage({ isOnline }) {
  return <p>{isOnline ? "在线" : "离线"}</p>;
}
```

## 7. 列表渲染

```jsx
function TodoList({ todos }) {
  return (
    <ul>
      {todos.map((todo) => (
        <li key={todo.id}>{todo.text}</li>
      ))}
    </ul>
  );
}

// 使用
const todos = [
  { id: 1, text: "学习 React" },
  { id: 2, text: "做项目" },
  { id: 3, text: "写文档" }
];
<TodoList todos={todos} />
```

## 8. 表单处理

```jsx
function Form() {
  const [formData, setFormData] = useState({
    name: "",
    email: ""
  });
  
  const handleChange = (e) => {
    const { name, value } = e.target;
    setFormData({
      ...formData,
      [name]: value
    });
  };
  
  const handleSubmit = (e) => {
    e.preventDefault();
    console.log(formData);
  };
  
  return (
    <form onSubmit={handleSubmit}>
      <input
        type="text"
        name="name"
        value={formData.name}
        onChange={handleChange}
        placeholder="输入名字"
      />
      <input
        type="email"
        name="email"
        value={formData.email}
        onChange={handleChange}
        placeholder="输入邮箱"
      />
      <button type="submit">提交</button>
    </form>
  );
}
```

## 9. 组件通信

### 父传子（通过 Props）

```jsx
function Parent() {
  return <Child message="从父组件传来的消息" />;
}

function Child({ message }) {
  return <p>{message}</p>;
}
```

### 子传父（通过回调函数）

```jsx
function Parent() {
  const handleChildClick = (data) => {
    console.log("子组件发送的数据：", data);
  };
  
  return <Child onSend={handleChildClick} />;
}

function Child({ onSend }) {
  return (
    <button onClick={() => onSend("你好，父组件！")}>
      发送数据
    </button>
  );
}
```

## 10. 样式处理

```jsx
// 内联样式
function StyledDiv() {
  const styles = {
    container: {
      backgroundColor: "#f0f0f0",
      padding: "20px",
      borderRadius: "8px"
    }
  };
  return <div style={styles.container}>样式化的 div</div>;
}

// 类名（需要 CSS 文件）
function Button() {
  return <button className="primary-btn">点击我</button>;
}
```

## 11. 完整示例：待办事项应用

```jsx
import { useState } from 'react';

function TodoApp() {
  const [todos, setTodos] = useState([]);
  const [input, setInput] = useState("");
  
  const addTodo = () => {
    if (input.trim()) {
      setTodos([...todos, { id: Date.now(), text: input }]);
      setInput("");
    }
  };
  
  const deleteTodo = (id) => {
    setTodos(todos.filter(todo => todo.id !== id));
  };
  
  return (
    <div>
      <h1>我的待办事项</h1>
      <input
        value={input}
        onChange={(e) => setInput(e.target.value)}
        placeholder="输入新任务"
      />
      <button onClick={addTodo}>添加</button>
      
      <ul>
        {todos.map(todo => (
          <li key={todo.id}>
            {todo.text}
            <button onClick={() => deleteTodo(todo.id)}>删除</button>
          </li>
        ))}
      </ul>
    </div>
  );
}

export default TodoApp;
```

## 12. React 的优势

✅ **声明式** - 描述 UI 应该是什么样子，而不是如何改变它  
✅ **组件化** - 代码复用性强  
✅ **高效** - 虚拟 DOM 优化性能  
✅ **单向数据流** - 数据流清晰易于调试  
✅ **生态丰富** - 大量第三方库和工具

## 13. 常用工具和库

- **Create React App** - 快速创建 React 项目
- **Next.js** - React 全栈框架
- **React Router** - 路由管理
- **Redux/Zustand** - 状态管理
- **Axios/Fetch** - 数据请求

---

React 的核心就是：**组件 + Props + State = 动态 UI**。如果你想学习更深入的内容（比如高级 Hooks、Context API、性能优化等），我可以继续讲解！