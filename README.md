# LifeTracker - 综合生活追踪应用程序

> 🚀 使用 Tauri + React + TypeScript + Rust 构建的现代化综合生活追踪桌面应用

LifeTracker 是一个功能强大的综合生活追踪工具，帮助您管理生活的各个方面：时间追踪、财务记录、日记写作、习惯打卡等。让您的生活更有条理，提高效率。

## ✨ 主要功能

### 🕒 时间追踪
- 精确的时间计算（基于系统时间戳）
- 任务分类和标签管理
- 暂停/恢复功能
- 实时状态同步

### 💰 财务管理
- 收入支出记录
- 分类统计
- 预算管理
- 财务报表

### 📝 日记功能
- 日常记录
- 心情追踪
- 富文本编辑
- 搜索和标签

### ✅ 习惯打卡
- 习惯追踪
- 连续打卡记录
- 进度可视化
- 目标设定

### 📊 数据统计
- 多维度分析
- 图表可视化
- 自定义报表
- 数据导出

## 🛠️ 技术栈

- **前端**: React 18 + TypeScript + Tailwind CSS + Vite
- **后端**: Rust + Tauri + SQLite
- **工具链**: Biome（代码格式化）+ pnpm（包管理）

## 🚀 快速开始

### 环境要求

- Node.js 18+
- Rust 1.75+
- pnpm 8+

### 安装依赖

```bash
git clone https://github.com/username/life-tracker.git
cd life-tracker
pnpm install
```

### 开发模式

```bash
# 启动开发服务器
pnpm tauri:dev
```

### 构建生产版本

```bash
# 构建应用
pnpm tauri:build
```

## 📁 项目结构

```
life-tracker/
├── src/
│   ├── components/          # React 组件
│   │   ├── Dashboard.tsx   # 主仪表板
│   │   ├── TaskManagement.tsx
│   │   ├── CategoryManagement.tsx
│   │   ├── Statistics.tsx
│   │   ├── Settings.tsx
│   │   ├── About.tsx
│   │   ├── TitleBar.tsx    # 自定义标题栏
│   │   └── ErrorBoundary.tsx
│   ├── hooks/              # 自定义 React Hooks
│   │   ├── useTheme.tsx    # 主题管理
│   │   └── useScrollbarHiding.tsx
│   ├── types/              # TypeScript 类型定义
│   │   └── index.ts        # 核心数据类型
│   ├── core/               # Rust 核心业务逻辑
│   ├── storage/            # 数据存储层
│   ├── config/             # 配置管理
│   ├── utils/              # 工具函数
│   └── errors.rs           # 错误处理
├── public/                 # 静态资源
├── icons/                  # 应用图标
└── docs/                   # 项目文档
```

## 💾 数据存储

应用数据存储在以下位置：

```
LifeTracker/
├── config.toml             # 应用配置
├── lifetracker.db         # SQLite 数据库
└── logs/                   # 应用日志
```

**数据目录位置**：
- **Windows**: `%APPDATA%\LifeTracker\`
- **macOS**: `~/Library/Application Support/lifetracker/`
- **Linux**: `~/.local/share/lifetracker/`

## 🎨 主题支持

- 🌞 浅色主题
- 🌙 深色主题
- 🎯 自动跟随系统

## 📊 数据导入导出

支持多种格式的数据导入导出：

- CSV 格式
- JSON 格式
- XML 格式
- Markdown 报告

## 🔧 开发指南

### 代码规范

- 使用 Biome 进行代码格式化
- 遵循 TypeScript 严格模式
- Rust 代码使用 clippy 检查

### 提交规范

```bash
# 功能开发
feat: 添加财务记录功能

# 问题修复
fix: 修复计时器暂停后无法继续的问题

# 性能优化
perf: 优化任务列表渲染性能
```

## 🤝 贡献

欢迎提交 Issue 和 Pull Request！

## 📄 许可证

MIT License

## 📞 联系方式

- 📧 Email: contact@lifetracker.dev
- 🌐 Website: https://lifetracker.dev
- 📱 GitHub: https://github.com/lifetracker/lifetracker

---

**LifeTracker** - 让生活更有条理 ✨