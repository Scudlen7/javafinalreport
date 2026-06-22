# 导师学生配对管理系统

导师与学生指导关系管理平台，前后端分离架构。本项目用于管理导师与学生的配对关系，包括本科毕设导师、研究生导师、双创项目指导、社团活动指导等，并详细记录了导师与学生配对后的产出成果和珍贵资料，如合影、奖项等。

## 技术栈

| 层级 | 技术 |
|------|------|
| 后端 | Java 21、Spring Boot 3.5.15、MyBatis Plus、Spring Security、JWT |
| 前端 | Vue 3、Vite、Element Plus、Pinia、Vue Router、Axios |
| 数据库 | MySQL 8.0 |

## 功能模块

- 导师信息管理
- 学生信息管理
- 师生关系配对（申请 / 审核 / 取消）
- 指导项目管理
- 成果资料管理（文件上传）
- 首页数据统计
- 用户权限管理（管理员 / 导师 / 学生）

## 快速开始

### 1. 环境要求

- JDK 21+
- Maven 3.8+
- MySQL 8.0
- Node.js 18+

### 2. 初始化数据库

> 新建数据库：`sql/supervisor_db.sql`
> 执行数据库升级脚本：
> `sql/alter_sys_user_add_email.sql`
> `sql/alter_student_add_gender.sql`
> `sql/alter_project_student.sql`
> `sql/alter_achievement_student.sql`
> `sql/alter_achievement_add_user_id.sql`

修改[`src/main/resources/application.properties`](src/main/resources/application.properties)中的数据库连接信息：

```properties
spring.datasource.url=jdbc:mysql://localhost:3306/supervisor_db?...
spring.datasource.username=root
spring.datasource.password=你的密码
```

### 3. 启动后端

```bash
mvn spring-boot:run
```

后端默认端口: **8081**

### 4. 启动前端

```bash
cd frontend
npm install
npm run dev
```

前端默认端口: **5173**，已配置代理转发到后端。

### 5. 访问系统

浏览器打开: http://localhost:5173

## 项目结构

```
supervisorstu/
├── sql/                    # 数据库脚本
├── docs/                   # API 文档
├── src/main/java/          # 后端源码
│   └── org/example/supervisorstu/
│       ├── controller/     # 控制器
│       ├── service/        # 业务层
│       ├── mapper/         # 数据访问
│       ├── entity/         # 实体类
│       ├── dto/            # 请求对象
│       ├── vo/             # 响应对象
│       ├── config/         # 配置
│       ├── security/       # 安全认证
│       ├── common/         # 公共组件
│       └── utils/          # 工具类
└── frontend/               # Vue3 前端
    └── src/
        ├── api/            # 接口封装
        ├── views/          # 页面
        ├── components/     # 组件
        ├── router/         # 路由
        ├── store/          # 状态管理
        └── utils/          # 工具
```

## 权限说明

- **管理员**: 全部功能
- **导师**: 管理自己的学生和项目，上传成果
- **学生**: 只能访问自己的数据和配对信息

## 相关文档

- [API 接口文档](docs/API.md)
- [部署说明](docs/DEPLOY.md)
