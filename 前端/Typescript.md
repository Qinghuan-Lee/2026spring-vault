# TypeScript 介绍

TypeScript 是 **JavaScript 的超集**，它在 JavaScript 的基础上添加了**静态类型检查**。简单来说，它让你在编写代码时就能发现错误，而不是等到运行时。

## 1. TypeScript 是什么？

```typescript
// JavaScript（无类型检查）
function add(a, b) {
  return a + b;
}
add(5, "10"); // 返回 "510"，这是个 bug！

// TypeScript（有类型检查）
function add(a: number, b: number): number {
  return a + b;
}
add(5, "10"); // ❌ 编译错误！类型不匹配
add(5, 10);   // ✅ 正确
```

TypeScript 代码需要被**编译**成 JavaScript 才能运行。

## 2. 基本类型

```typescript
// 基本类型
let name: string = "张三";
let age: number = 25;
let isActive: boolean = true;
let nothing: null = null;
let undefined: undefined = undefined;

// 数组
let numbers: number[] = [1, 2, 3];
let strings: Array<string> = ["a", "b", "c"];

// 任意类型（不推荐）
let anything: any = "可以是任何值";

// unknown（比 any 更安全）
let value: unknown = "something";
// value.toUpperCase(); // ❌ 错误，必须先检查类型
if (typeof value === "string") {
  value.toUpperCase(); // ✅ 现在安全了
}
```

## 3. 联合类型（Union Types）

```typescript
// 允许多种类型中的一种
let id: number | string;
id = 123;      // ✅
id = "ABC123"; // ✅
id = true;     // ❌ 类型错误

// 函数参数
function printId(id: number | string) {
  if (typeof id === "string") {
    console.log("字符串 ID：" + id.toUpperCase());
  } else {
    console.log("数字 ID：" + id);
  }
}
```

## 4. 接口（Interface）

接口定义对象的结构。

```typescript
// 定义接口
interface User {
  name: string;
  age: number;
  email?: string; // ? 表示可选属性
}

// 使用接口
const user: User = {
  name: "Alice",
  age: 25
  // email 是可选的，可以不写
};

// 错误示例
const wrongUser: User = {
  name: "Bob",
  // ❌ 缺少 age 属性
};
```

## 5. 类型别名（Type Alias）

```typescript
// 定义类型别名
type ID = string | number;
type Status = "active" | "inactive" | "pending";

let userId: ID = 123;
let userStatus: Status = "active";
userStatus = "deleted"; // ❌ 错误

// 对象类型
type Person = {
  name: string;
  age: number;
};

const person: Person = {
  name: "张三",
  age: 30
};
```

## 6. 枚举（Enum）

```typescript
// 数字枚举
enum Direction {
  Up = 0,
  Down = 1,
  Left = 2,
  Right = 3
}

let dir: Direction = Direction.Up;

// 字符串枚举（更常用）
enum Status {
  Active = "ACTIVE",
  Inactive = "INACTIVE",
  Pending = "PENDING"
}

let status: Status = Status.Active;
```

## 7. 函数类型

```typescript
// 指定参数和返回值类型
function add(a: number, b: number): number {
  return a + b;
}

// 可选参数（使用 ?）
function greet(name: string, greeting?: string): void {
  console.log(greeting ? greeting + name : "你好 " + name);
}

// 默认参数
function multiply(a: number, b: number = 2): number {
  return a * b;
}

// 函数类型
type Callback = (data: string) => void;
const handleData: Callback = (data) => {
  console.log(data);
};

// 箭头函数类型
type Calculate = (a: number, b: number) => number;
const subtract: Calculate = (a, b) => a - b;
```

## 8. 类（Class）

```typescript
class Animal {
  // 属性
  name: string;
  age: number;
  
  // 构造方法
  constructor(name: string, age: number) {
    this.name = name;
    this.age = age;
  }
  
  // 方法
  speak(): void {
    console.log(`${this.name} 发出声音`);
  }
}

// 继承
class Dog extends Animal {
  breed: string;
  
  constructor(name: string, age: number, breed: string) {
    super(name, age); // 调用父类构造方法
    this.breed = breed;
  }
  
  speak(): void {
    console.log(`${this.name} 汪汪叫`);
  }
}

const dog = new Dog("旺财", 3, "柴犬");
dog.speak(); // 输出：旺财 汪汪叫
```

## 9. 访问修饰符

```typescript
class Person {
  public name: string;      // 公开
  private age: number;       // 私有
  protected email: string;   // 受保护
  readonly id: number;       // 只读
  
  constructor(name: string, age: number, email: string, id: number) {
    this.name = name;
    this.age = age;
    this.email = email;
    this.id = id;
  }
  
  getAge(): number {
    return this.age;
  }
}

const person = new Person("Alice", 25, "alice@example.com", 1);
console.log(person.name);  // ✅
console.log(person.age);   // ❌ 私有属性，不能访问
person.id = 2;             // ❌ 只读属性，不能修改
```

## 10. 泛型（Generics）

泛型让你编写可复用的、与类型无关的代码。

```typescript
// 基本泛型
function getFirstElement<T>(arr: T[]): T {
  return arr[0];
}

const firstNum = getFirstElement<number>([1, 2, 3]); // 类型是 number
const firstStr = getFirstElement<string>(["a", "b"]); // 类型是 string

// 泛型接口
interface Container<T> {
  value: T;
  getValue(): T;
}

const numberContainer: Container<number> = {
  value: 42,
  getValue() {
    return this.value;
  }
};

// 泛型类
class Stack<T> {
  private items: T[] = [];
  
  push(item: T): void {
    this.items.push(item);
  }
  
  pop(): T | undefined {
    return this.items.pop();
  }
}

const numStack = new Stack<number>();
numStack.push(1);
numStack.push(2);
```

## 11. React + TypeScript

```typescript
import React, { useState } from 'react';

// 定义 Props 类型
interface ButtonProps {
  label: string;
  onClick: () => void;
  disabled?: boolean;
}

// 组件
const Button: React.FC<ButtonProps> = ({ label, onClick, disabled }) => {
  return (
    <button onClick={onClick} disabled={disabled}>
      {label}
    </button>
  );
};

// 使用 State 和类型
function Counter() {
  const [count, setCount] = useState<number>(0);
  
  return (
    <div>
      <p>计数：{count}</p>
      <Button 
        label="增加" 
        onClick={() => setCount(count + 1)}
      />
    </div>
  );
}
```

## 12. 实用的高级类型

```typescript
// Partial - 使所有属性可选
interface Config {
  host: string;
  port: number;
}
type PartialConfig = Partial<Config>; // 所有属性都是可选的

// Required - 使所有属性必需
type RequiredConfig = Required<PartialConfig>; // 所有属性都是必需的

// Pick - 选择某些属性
type BasicConfig = Pick<Config, 'host'>; // 只有 host

// Omit - 排除某些属性
type SimpleConfig = Omit<Config, 'port'>; // 除了 port

// Record - 创建映射类型
type Role = 'admin' | 'user' | 'guest';
type Permissions = Record<Role, string[]>;
const perms: Permissions = {
  admin: ['read', 'write', 'delete'],
  user: ['read'],
  guest: []
};
```

## 13. TypeScript vs JavaScript

|特性|JavaScript|TypeScript|
|---|---|---|
|类型检查|运行时|编译时|
|错误发现|运行时才发现|编写时就发现|
|学习曲线|简单|有一定难度|
|代码提示|一般|很好（IDE 支持）|
|编译|不需要|需要编译成 JS|

## 14. TypeScript 项目设置

```bash
# 安装 TypeScript
npm install -g typescript

# 创建 tsconfig.json
tsc --init

# 编译 TypeScript 文件
tsc

# 监听文件变化自动编译
tsc --watch
```

## 15. 完整示例

```typescript
// 定义用户接口
interface User {
  id: number;
  name: string;
  email: string;
  roles: string[];
}

// 定义 API 响应类型
interface ApiResponse<T> {
  code: number;
  message: string;
  data: T;
}

// 用户服务类
class UserService {
  async getUser(id: number): Promise<User> {
    const response = await fetch(`/api/users/${id}`);
    const result: ApiResponse<User> = await response.json();
    return result.data;
  }
  
  async getUsers(): Promise<User[]> {
    const response = await fetch('/api/users');
    const result: ApiResponse<User[]> = await response.json();
    return result.data;
  }
}

// 使用
const userService = new UserService();
userService.getUser(1).then(user => {
  console.log(user.name); // IDE 会提示 name 属性
});
```

## TypeScript 的核心优势

✅ **早期发现错误** - 编译时就能发现类型错误  
✅ **更好的 IDE 支持** - 自动补全和参数提示  
✅ **代码可读性** - 类型注解使代码更清晰  
✅ **重构更安全** - 修改代码时能快速发现问题  
✅ **更好的团队协作** - 类型文档化接口和 API

---

简单来说：**TypeScript = JavaScript + 类型系统**。它在保留 JavaScript 灵活性的同时，加入了类型安全。许多大型项目（React、Angular、Vue 3 等）都用 TypeScript 编写！

有什么不明白的地方吗？😊