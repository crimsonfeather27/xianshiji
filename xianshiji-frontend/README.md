# 鲜食记 xianshiji · 前端

家庭食材库存管理与菜谱推荐应用的移动端，基于 **Expo + React Native + TypeScript**，配合 Spring Boot 后端使用。

## 技术栈

| 类别 | 选型 |
|---|---|
| 框架 | Expo SDK 54 + React Native 0.81 + React 19.1 |
| 语言 | TypeScript |
| 路由 | expo-router 6（文件路由） |
| 硬件能力 | expo-camera（扫码录入）、expo-image-picker |
| 本地存储 | @react-native-async-storage/async-storage |

## 核心功能

- 用户注册 / 登录
- 食材库存管理：手动录入、扫码录入、分类 / 状态筛选、关键词搜索、库存统计
- 菜谱浏览：列表、详情、按菜系筛选、关键词搜索、添加菜谱
- 首页美食轮播图
- 家庭组（后端已支持创建 / 加入）

## 目录结构

```
app/                 # 文件路由（页面）
  (tabs)/            # 主导航 5 个 Tab：首页 / 库存管理 / 扫描 / 消息 / 我的
  login.tsx          # 登录
  register.tsx       # 注册
  recipes.tsx        # 菜谱列表
  recipe-detail.tsx  # 菜谱详情
  recipe-add.tsx     # 添加菜谱
  manual-add.tsx     # 手动录入食材
components/          # 通用组件
constants/
  api.ts             # 后端 API 地址配置（入口）
  theme.ts           # 主题色
hooks/               # 自定义 hooks
```

## 快速开始

### 1. 环境要求

- Node.js 18+（推荐 20 LTS）
- 手机安装 [Expo Go](https://expo.dev/go)

### 2. 安装依赖

```bash
npm install
```

### 3. 配置后端地址

后端默认运行在 `http://localhost:8080`（仓库内 `xianshiji-backend/`）。

真机调试时修改 [constants/api.ts](constants/api.ts) 中的默认地址为本机局域网 IP，或使用环境变量：

```powershell
$env:EXPO_PUBLIC_API_BASE_URL="http://192.168.x.x:8080"
```

查看本机 IP：`ipconfig`（取 WLAN 适配器 IPv4）。

### 4. 启动

```bash
npx expo start
```

- 手机用 Expo Go 扫码运行
- 或按 `a`（Android 模拟器）/ `i`（iOS 模拟器）/ `w`（Web）

## 说明

- 本项目为课程作业改造版，三人协作开发，作者（crimsonfeather27）负责菜谱模块全栈实现、食材录入与扫码功能，详见仓库根目录 `MY_CONTRIBUTION.md`
- 后端部分见 `../xianshiji-backend/`，项目整体说明见根目录 `PROJECT_OVERVIEW.md`
