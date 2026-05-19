# 什么是Springboot
Spring Boot 是一个基于 **Spring Framework** 的开源框架，用于快速构建独立的、生产级别的 Spring 应用程序。它由 Pivotal 团队（现属于 VMware）开发。

## 1. **核心特性**

### 快速开发

- **自动配置**：根据你添加的依赖自动配置 Spring 应用
- **约定优于配置**：遵循默认约定，减少配置文件
- **内嵌服务器**：内置 Tomcat、Jetty 等，无需部署到外部服务器


# Springboot 与java的关系

>Java = 砖头和水泥（原材料）
>Spring = 建筑工具和规范（如何组织使用）
> Spring Boot = 预制房屋（直接用，几乎不用改）

### 1. **层级关系图**

```
Java 语言
    ↓
JDK（Java 开发工具包）
    ↓
Spring Framework（Spring 框架）
    ↓
Spring Boot（快速开发框架）
```

### 2. **基本关系**

#### Java 是基础

- **Java** 是一门编程语言，Spring Boot 是用 Java 语言编写的框架
- Spring Boot 应用最终都编译成 Java 字节码（.class 文件）运行在 JVM 上
- 不懂 Java 就无法使用 Spring Boot

#### Spring Framework 是中间层

- **Spring Framework** 是 Java 的一个大型企业级框架，提供了：
    - 依赖注入（DI）
    - 面向切面编程（AOP）
    - 事务管理
    - MVC Web 框架

#### Spring Boot 是上层应用

- **Spring Boot** 是在 Spring Framework 基础上的**自动化解决方案**
- 简化了 Spring Framework 繁琐的配置
- 提供开箱即用的功能