
>in:description python stars:>500 pushed:>2025
# argparse

`argparse` 是 Python 标准库中的一个模块，专门用于**编写命令行接口**。

示例

```python
import argparse

# 1. 创建解析器
parser = argparse.ArgumentParser(description="一个简单的问候程序")

# 2. 定义想要接收的参数
parser.add_argument("--name", type=str, default="World", help="要问候的人的名字")

# 3. 解析参数
args = parser.parse_args()

# 4. 使用参数
print(f"Hello, {args.name}!")
```
# sys

\`sys` 是 Python 标准库中的一个**核心系统模块**。

`import sys` 让你能够与 Python 解释器本身、以及你的程序运行的操作系统环境进行交互。
