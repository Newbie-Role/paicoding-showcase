# 技术派 - 技术内容分享平台

基于 Spring Boot 的社区平台，用于技术内容分享。

## 项目简介

技术派是一个专注于技术内容分享的社区平台，提供文章发布、讨论、点赞等功能，旨在打造一个高质量的技术交流社区。

## 核心功能

- **文章管理**：支持发布、编辑、删除技术文章，支持 Markdown 格式
- **用户系统**：完整的用户注册、登录、个人资料管理功能
- **互动功能**：文章评论、点赞、收藏等社交功能
- **搜索系统**：基于 ElasticSearch 的全文搜索功能
- **文件上传**：支持图片上传、文件管理
- **系统管理**：后台管理系统，支持用户管理、内容审核等

## 技术栈

### 后端技术
- Spring Boot 2.7.1
- Java 8+
- MyBatis-Plus
- MySQL
- Redis
- ElasticSearch
- RabbitMQ
- MongoDB
- Liquibase

### 前端技术
- Thymeleaf
- JavaScript
- CSS3
- jQuery
- Editor.md

## 项目结构

```
paicoding-web              # Web 模块（控制器、REST 端点）
├── depends on: paicoding-ui, paicoding-service
│
paicoding-service          # 服务模块（业务逻辑）
├── depends on: paicoding-core, paicoding-api
│
paicoding-core             # 核心模块（工具类、通用组件）
├── depends on: paicoding-api
│
paicoding-api              # API 模块（实体、DTO、VO、枚举）
└── (base module: entities, DTOs, VOs, enums)

paicoding-ui               # UI 模块（Thymeleaf 模板、前端资源）
```

## 快速开始

### 环境要求
- JDK 8+
- Maven 3.6+
- MySQL 5.7+
- Redis (可选)
- ElasticSearch (可选)
- RabbitMQ (可选)
- MongoDB (可选)

### 安装步骤

```bash
# 1. 克隆仓库
git clone https://github.com/Newbie-RoleNewbie-Role/paicoding.git

# 2. 进入项目目录
cd paicoding

# 3. 构建项目
mvn clean package

# 4. 运行项目
java -jar paicoding-web/target/paicoding-web-1.0.0.jar

# 5. 访问项目
# 浏览器打开: http://localhost:8080
```

## 配置说明

项目配置文件位于 `paicoding-web/src/main/resources-env/` 目录，根据环境选择对应配置：

- `dev`：开发环境
- `test`：测试环境
- `pre`：预发环境
- `prod`：生产环境

### 主要配置项

#### 数据库配置 (`application-dal.yml`)
- 数据库连接信息
- MyBatis 配置

#### 图片上传配置 (`application-image.yml`)
- 本地存储路径
- CDN 配置
- OSS 配置

#### Web 配置 (`application-web.yml`)
- 服务器端口
- 上下文路径
- 会话配置

## 开发指南

### 代码规范
- 使用 Java 8+ 语法
- 遵循 Spring Boot 编码规范
- 添加适当的注释和文档
- 确保代码通过单元测试

### 数据库变更
- 添加 Liquibase changesets 到 `paicoding-web/src/main/resources/liquibase`
- 数据库会在首次启动时自动创建（默认：`paicoding`）
- 使用 MyBatis-Plus 进行数据库操作
- 实体类定义在 paicoding-api 模块

### 添加新功能
- 遵循分层架构：API → Service → Core
- 检查相邻文件中的现有代码模式
- 使用项目中已存在的库（检查根目录 `pom.xml`）
- 前端更改在 paicoding-ui 模块中进行

## API 文档

- Swagger UI 可在 `/doc.html` 访问
- 使用 Knife4j (knife4j-openapi2-spring-boot-starter)

## 测试

- 支持 JUnit 和 Spock（基于 Groovy 的 BDD）
- 测试文件在 `paicoding-web/src/test/java` 和 `paicoding-web/src/test/groovy`

## 部署

### 本地开发
- 直接运行 `QuickForumApplication` 类
- 或使用 `mvn spring-boot:run`

### 生产部署
1. 构建项目：`mvn clean package`
2. 复制 `paicoding-web/target/paicoding-web-1.0.0.jar` 到服务器
3. 运行：`java -jar paicoding-web-1.0.0.jar --spring.profiles.active=prod`

## 贡献指南

欢迎通过以下方式贡献项目：
- 提交 Issue 报告 bug 或建议新功能
- 提交 Pull Request 修复 bug 或添加新功能
- 改进文档和示例
- 分享项目，帮助更多开发者了解技术派

## 许可证

MIT License


