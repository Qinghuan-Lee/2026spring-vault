

# 关键差异总结


| 任务        | CMD             | PowerShell                       |
| --------- | --------------- | -------------------------------- |
| **创建文件夹** | `mkdir`         | `New-Item -ItemType Directory`   |
| **删除文件**  | `del file.txt`  | `Remove-Item file.txt`           |
| **列出文件**  | `dir`           | `Get-ChildItem`                  |
| **查看文件**  | `type`          | `Get-Content` / `cat`            |
| **过滤**    | `findstr`       | `Where-Object` / `Select-String` |
| **管道处理**  | 基础              | 强大的对象管道                          |
| **变量**    | `%var%`         | `$var`                           |
| **条件**    | `if...else`     | `if...elseif...else`             |
| **循环**    | `for`           | `for`, `foreach`, `while`        |
| **脚本扩展名** | `.bat` / `.cmd` | `.ps1`                           |
