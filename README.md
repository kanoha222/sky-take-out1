# Sky Take-Out

Sky Take-Out 是一个基于 Spring Boot 的在线餐饮点餐系统，为餐饮商家和消费者提供完整的线上点餐、订单管理、用户登录和支付功能。该项目包含了后端 API 的开发、缓存管理、JWT 鉴权、以及与第三方支付服务的集成，适用于中小型餐饮企业的线上点餐需求。

## 功能概述

### 1. 用户与权限管理
- **用户登录**：支持微信登录，生成并验证 JWT 令牌，确保用户会话的安全性。
- **管理员功能**：分配给餐饮商家管理员，用于管理菜单、订单和店铺状态。
- **权限控制**：基于角色的访问控制，确保不同用户仅能访问符合权限的内容和操作。

### 2. 菜品与套餐管理
- **菜品管理**：增删改查菜品信息，支持分页查询、根据分类筛选，并对数据进行缓存处理。
- **套餐管理**：支持创建和管理套餐，将多个菜品组合到一个套餐，便于消费者快速选择。
- **分类管理**：支持分类的增删改查操作，使得商家可以更灵活地管理菜品和套餐。

### 3. 订单管理
- **下单流程**：用户选择菜品或套餐后生成订单，支持订单提交、状态跟踪等功能。
- **订单状态**：订单状态包括待付款、已接单、配送中、已完成、已取消等状态。
- **支付功能**：集成微信支付接口，完成订单的支付和状态更新。
- **催单和取消**：用户可以在订单未完成之前选择催单或取消订单，订单取消需记录取消原因。

### 4. 数据缓存与性能优化
- **Redis 缓存**：利用 Redis 缓存菜品和套餐数据，减少数据库查询，提升系统响应速度。
- **缓存管理**：通过设置缓存失效和清除机制，确保菜品、套餐等信息的实时性和准确性。

## 技术栈

- **后端框架**：Spring Boot
- **持久层框架**：MyBatis
- **缓存**：Redis
- **安全与认证**：JWT（JSON Web Token）
- **支付集成**：微信支付 API
- **数据库**：MySQL

## 文件结构

```plaintext
sky-take-out/
├── sky-common/                # 公共模块，包含常量、异常处理、工具类等
├── sky-pojo/                  # 数据传输对象（DTO）、实体类、返回值对象（VO）
├── sky-server/                # 核心服务模块，包含控制器、服务层、数据访问层等
│   ├── src/main/java/com/sky/
│   │   ├── controller/         # 控制器层，定义用户和管理员的 API 接口
│   │   ├── service/            # 服务层，包含业务逻辑和具体服务实现
│   │   ├── mapper/             # 数据访问层，定义 MyBatis 接口
│   │   ├── config/             # 配置类，包含 Redis 配置、任务调度等
│   │   └── task/               # 定时任务模块，执行定时操作
│   └── src/main/resources/
│       ├── application.yml     # 通用配置文件
│       ├── application-dev.yml # 开发环境配置
│       └── mapper/             # MyBatis Mapper XML 文件
└── pom.xml                     # Maven 项目配置文件

