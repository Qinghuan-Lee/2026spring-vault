MySQL 是一个广泛使用的开源关系型数据库管理系统。

## 基本概念

**MySQL** 是一种 SQL（结构化查询语言）数据库，用于存储、管理和检索数据。它基于客户端-服务器架构，采用表格形式组织数据。

## 主要特点

- **开源免费** — 源代码公开，可自由使用和修改
- **跨平台** — 可在 Linux、Windows、macOS 等多个操作系统上运行
- **高性能** — 查询速度快，适合大多数 Web 应用
- **可靠性强** — 支持事务处理、数据备份和恢复
- **易于使用** — SQL 语法相对简单，学习曲线平缓

## 核心概念

|概念|说明|
|---|---|
|**数据库**|存储相关数据表的容器|
|**表**|由行和列组成的数据结构|
|**行（记录）**|表中的一条数据记录|
|**列（字段）**|表中具有特定数据类型的属性|
|**主键**|唯一标识每条记录的字段|

## 常见用途

- Web 应用后端数据库（如 WordPress、Drupal）
- 内容管理系统（CMS）
- 电商平台
- 数据分析和报表系统
- 日志系统

## 基本操作示例

```sql
-- 创建数据库
CREATE DATABASE mydb;

-- 创建表
CREATE TABLE users (
  id INT PRIMARY KEY AUTO_INCREMENT,
  name VARCHAR(100),
  email VARCHAR(100),
  age INT
);

-- 插入数据
INSERT INTO users (name, email, age) VALUES ('张三', 'zhangsan@example.com', 25);

-- 查询数据
SELECT * FROM users WHERE age > 20;

-- 更新数据
UPDATE users SET age = 26 WHERE name = '张三';

-- 删除数据
DELETE FROM users WHERE id = 1;
```

## 版本和变体

- **MySQL 5.7/8.0** — 官方稳定版本
- **MariaDB** — MySQL 的开源分支，兼容性好
- **Percona Server** — 针对性能优化的 MySQL 变体

## 适用场景 vs 不适用场景

**适合：** 结构化数据、中小型应用、Web 开发 **不适合：** 非结构化大数据、实时流处理、超大规模分布式系统

有什么关于 MySQL 的具体问题吗？比如安装、配置、优化或某个特定功能？