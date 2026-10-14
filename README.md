# 鲜食记 xianshiji

家庭食材库存管理与菜谱推荐的全栈移动应用。

前端基于 **Expo + React Native + TypeScript**，后端基于 **Spring Boot + MyBatis + MySQL**，支持食材库存管理、扫码录入、菜谱浏览与家庭组共享。

> 三人协作课程项目，作者（[crimsonfeather27](https://github.com/crimsonfeather27)）负责**菜谱模块全栈实现**与**食材录入 / 扫码功能**，详见[个人贡献](#个人贡献)。

## 核心功能

- **食材库存管理**：手动录入、条形码扫码录入（expo-camera）、分类 / 状态筛选、关键词搜索、库存统计、保底量提醒
- **菜谱管理**：菜谱列表 / 详情 / 添加，配料关联，按菜系筛选，关键词搜索
- **用户系统**：手机号 / 邮箱注册登录，头像上传
- **家庭组**：邀请码创建 / 加入家庭组

## 技术栈

| 端 | 技术 |
|---|---|
| 前端 | Expo SDK 54 · React Native 0.81 · React 19 · TypeScript · expo-router（文件路由）· AsyncStorage |
| 后端 | Spring Boot 4 · MyBatis（XML Mapper）· Java 17 · Maven |
| 数据库 | MySQL 8.0（7 张表：用户 / 家庭组 / 成员关系 / 食材 / 菜谱 / 配料 / 收藏） |

## 项目结构

```
xianshiji/
├── xianshiji-frontend/     # Expo 移动端（详见子目录 README）
│   ├── app/                # 文件路由页面（5 主 Tab + 菜谱/录入等）
│   ├── components/         # 通用组件
│   └── constants/api.ts    # 后端 API 地址配置
└── xianshiji-backend/
    ├── database.sql        # 数据库表结构 DDL
    └── xianshiji/          # Spring Boot 后端
        └── src/main/
            ├── java/.../   # controller / service / mapper / entity
            └── resources/  # application.yml + MyBatis XML
```

## 快速启动

### 后端（端口 8080）

```bash
cd xianshiji-backend/xianshiji
./mvnw spring-boot:run        # Windows: .\mvnw.cmd spring-boot:run
```

数据库配置见 `src/main/resources/application.yml`，表结构导入 `xianshiji-backend/database.sql`。

### 前端

```bash
cd xianshiji-frontend
npm install
npx expo start                # 手机 Expo Go 扫码运行
```

真机调试时将 `xianshiji-frontend/constants/api.ts` 中地址改为本机局域网 IP，或设置环境变量 `EXPO_PUBLIC_API_BASE_URL`。

详细说明见 [xianshiji-frontend/README.md](xianshiji-frontend/README.md)。

## 个人贡献

本项目为三人协作开发，我（crimsonfeather27）独立负责：

- **后端菜谱模块从 0 到 1**：RecipeController 8 个 REST 接口（CRUD / 配料关联 / 菜系筛选 / 关键词搜索）+ Service 业务编排 + MyBatis XML 手写 SQL 映射
- **前端菜谱全链路**：菜谱列表、详情、添加三个页面（expo-router）
- **食材录入功能**：手动录入表单页 + expo-camera 扫码录入 Tab 页
- **首页轮播**：分页滚动 + 圆点指示器的美食图片轮播

其他同学负责：用户 / 库存管理 / 家庭组模块。
