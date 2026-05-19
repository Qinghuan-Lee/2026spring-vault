# Go 语言语法介绍

Go（Golang）是一门由 Google 开发的编程语言，以其简洁高效著称。下面我为你介绍主要的语法特性：

## 1. **基本数据类型**

```go
// 布尔类型
var b bool = true

// 整数类型
var i int = 42
var u uint = 10
var i8 int8 = 127
var i64 int64 = 9223372036854775807

// 浮点类型
var f float32 = 3.14
var f64 float64 = 3.14159

// 字符串
var s string = "Hello, Go!"

// 短声明（函数内）
x := 10
```

## 2. **变量和常量**

```go
// 变量声明
var a int
var b, c int = 1, 2
var d = 3  // 类型推断

// 短声明（只在函数内）
e := 4

// 常量
const PI = 3.14159
const (
    Red = 0
    Green = 1
    Blue = 2
)
```

## 3. **函数**

```go
// 基础函数
func add(x int, y int) int {
    return x + y
}

// 多返回值
func divide(x, y float64) (float64, error) {
    if y == 0 {
        return 0, fmt.Errorf("除数不能为0")
    }
    return x / y, nil
}

// 命名返回值
func swap(x, y string) (a, b string) {
    a = y
    b = x
    return  // 直接返回，自动返回 a, b
}

// 可变参数
func sum(nums ...int) int {
    total := 0
    for _, num := range nums {
        total += num
    }
    return total
}
```

## 4. **控制流**

```go
// if-else
if x > 0 {
    fmt.Println("正数")
} else if x < 0 {
    fmt.Println("负数")
} else {
    fmt.Println("零")
}

// switch
switch os := runtime.GOOS; os {
case "darwin":
    fmt.Println("macOS")
case "linux":
    fmt.Println("Linux")
default:
    fmt.Println("其他系统")
}

// for 循环（Go 只有 for，没有 while）
for i := 0; i < 10; i++ {
    fmt.Println(i)
}

// range 循环
arr := []int{1, 2, 3, 4, 5}
for i, v := range arr {
    fmt.Printf("索引: %d, 值: %d\n", i, v)
}

// 无限循环
for {
    // break 跳出
}
```

## 5. **数组和切片**

```go
// 数组（长度固定）
var arr [5]int = [5]int{1, 2, 3, 4, 5}
arr2 := [...]string{"a", "b", "c"}

// 切片（动态数组）
var slice []int
slice = []int{1, 2, 3}
slice = append(slice, 4, 5)

// 切片操作
s := []int{0, 1, 2, 3, 4, 5}
s[1:4]      // [1 2 3] （包含 1，不包含 4）
s[:3]       // [0 1 2]
s[3:]       // [3 4 5]
s[:]        // [0 1 2 3 4 5]

// make 创建切片
slice := make([]int, 5, 10)  // 长度 5，容量 10
```

## 6. **映射（Map）**

```go
// 声明 map
var m map[string]int
m = make(map[string]int)

// 初始化 map
m := map[string]int{
    "a": 1,
    "b": 2,
    "c": 3,
}

// 操作
m["d"] = 4
delete(m, "a")
v, ok := m["a"]  // 检查 key 是否存在
```

## 7. **结构体**

```go
type Person struct {
    Name string
    Age  int
}

// 创建结构体
p := Person{"Alice", 30}
p := Person{Name: "Bob", Age: 25}

// 访问字段
fmt.Println(p.Name)
p.Age = 31
```

## 8. **指针**

```go
x := 10
p := &x      // 取地址
fmt.Println(*p)  // 解引用
*p = 20      // 修改指向的值

// 指针接收者可以修改原值
type Counter struct {
    count int
}

func (c *Counter) Increment() {
    c.count++
}
```

## 9. **接口**

```go
type Reader interface {
    Read(p []byte) (n int, err error)
}

type Writer interface {
    Write(p []byte) (n int, err error)
}

// 实现接口（隐式）
type MyWriter struct{}

func (w MyWriter) Write(p []byte) (n int, err error) {
    fmt.Println(string(p))
    return len(p), nil
}
```

## 10. **错误处理**

```go
// Go 使用显式的错误返回
func OpenFile(name string) (*File, error) {
    if name == "" {
        return nil, fmt.Errorf("文件名不能为空")
    }
    // ...
}

// 常见的错误处理模式
if err != nil {
    log.Fatal(err)
}
```

## 11. **并发（Goroutines 和 Channels）**

```go
// Goroutine（轻量级线程）
go func() {
    fmt.Println("在后台运行")
}()

// Channel（通信管道）
ch := make(chan int)

go func() {
    ch <- 42  // 发送
}()

value := <-ch  // 接收

// 关闭 channel
close(ch)
```

## 12. **defer、panic、recover**

```go
func main() {
    defer fmt.Println("3. 最后执行")
    fmt.Println("1. 先执行")
    
    if true {
        panic("出错了")  // 会跳到 recover
    }
    fmt.Println("2. 不会执行")
}

// 恢复
defer func() {
    if r := recover(); r != nil {
        fmt.Println("捕获错误:", r)
    }
}()
```

Go 的语法设计很简洁，这是它的一个重要特性。有什么想深入了解的吗？