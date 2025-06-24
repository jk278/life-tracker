# 个人时间追踪器开发指导文档

## 📋 项目概述

**项目名称**: TimeTracker (个人时间追踪器)  
**项目类型**: 桌面应用 + CLI工具  
**开发周期**: 3-4周  
**学习目标**: 通过构建实用的时间管理工具掌握Rust核心概念

## 🎯 为什么选择时间追踪器？

### 日常实用性
- ✅ **真正会用到** - 提高工作效率，管理时间
- ✅ **即时反馈** - 每次使用都能看到数据变化
- ✅ **持续改进** - 根据使用体验不断优化功能
- ✅ **数据驱动** - 通过数据了解自己的时间分配

### 技术学习价值
- 🔥 **GUI开发** - 学习现代桌面应用开发
- 🔥 **数据持久化** - 数据库操作和文件存储
- 🔥 **异步编程** - 定时器和后台任务
- 🔥 **系统集成** - 系统通知和快捷键

## 🚀 功能特性设计

### 核心功能 (第1-2周)
- [ ] **任务计时**
  - 开始/暂停/停止计时
  - 任务分类和标签
  - 手动时间调整
- [ ] **数据记录**
  - 本地数据库存储
  - 时间段记录
  - 任务描述和备注
- [ ] **基础统计**
  - 日/周/月统计
  - 分类时间占比
  - 简单图表展示

### 增强功能 (第3周)
- [ ] **智能提醒**
  - 番茄钟模式 (25分钟工作 + 5分钟休息)
  - 自定义提醒间隔
  - 系统通知
- [ ] **数据分析**
  - 效率趋势分析
  - 时间分配优化建议
  - 目标设定和追踪
- [ ] **导入导出**
  - CSV格式导出
  - 数据备份和恢复
  - 多设备同步准备

### 高级功能 (第4周)
- [ ] **GUI界面**
  - 现代化桌面界面
  - 系统托盘集成
  - 快捷键支持
- [ ] **自动化**
  - 应用程序监控
  - 自动分类建议
  - 空闲时间检测

## 🏗️ 技术架构

### 项目结构
```
time_tracker/
├── Cargo.toml              # Rust项目配置
├── package.json            # 前端项目配置
├── tauri.conf.json         # Tauri应用配置
├── index.html              # HTML入口文件
├── vite.config.ts          # Vite构建配置
├── tailwind.config.js      # Tailwind CSS配置
├── README.md               # 项目说明
├── src/
│   ├── main.rs            # Rust程序入口
│   ├── lib.rs             # Rust库文件
│   ├── tauri_commands.rs  # Tauri命令定义
│   ├── App.tsx            # React主应用组件
│   ├── main.tsx           # React入口文件
│   ├── index.css          # 样式文件
│   ├── components/        # React组件
│   │   ├── Dashboard.tsx  # 仪表板组件
│   │   ├── TaskManagement.tsx # 任务管理组件
│   │   ├── CategoryManagement.tsx # 分类管理组件
│   │   ├── Statistics.tsx # 统计报告组件
│   │   ├── Settings.tsx   # 设置组件
│   │   └── About.tsx      # 关于组件
│   ├── hooks/             # React Hooks
│   │   └── useTheme.tsx   # 主题Hook
│   ├── types/             # TypeScript类型定义
│   │   └── index.ts       # 类型定义文件
│   ├── core/              # 核心逻辑
│   │   ├── mod.rs
│   │   ├── timer.rs       # 计时器逻辑
│   │   ├── task.rs        # 任务管理
│   │   ├── category.rs    # 分类管理
│   │   └── analytics.rs   # 数据分析
│   ├── storage/           # 数据存储
│   │   ├── mod.rs
│   │   ├── database.rs    # 数据库操作
│   │   ├── models.rs      # 数据模型
│   │   ├── task_models.rs # 任务模型
│   │   └── migrations.rs  # 数据库迁移
│   ├── config/            # 配置管理
│   │   ├── mod.rs
│   │   ├── settings.rs    # 设置管理
│   │   └── theme.rs       # 主题配置
│   ├── utils/             # 工具函数
│   │   ├── mod.rs
│   │   ├── date.rs        # 时间处理
│   │   ├── format.rs      # 格式化工具
│   │   ├── validation.rs  # 数据验证
│   │   ├── export.rs      # 数据导出
│   │   └── import.rs      # 数据导入
│   └── errors.rs          # 错误处理
└── assets/                # 资源文件
    └── icons/
        └── icon.ico       # 应用图标
```

### 核心依赖
```toml
[dependencies]
# Tauri 核心依赖
tauri = { version = "2.5.1", features = ["tray-icon"] }
tauri-plugin-shell = "2.2"
tauri-plugin-notification = "2.2"

# 数据库
rusqlite = { version = "0.29", features = ["bundled", "backup"] }
serde = { version = "1.0", features = ["derive"] }
serde_json = "1.0"         # JSON序列化

# 时间处理
chrono = { version = "0.4", features = ["serde"] }
tokio = { version = "1.0", features = ["full"] }  # 异步运行时

# CLI
clap = { version = "4.0", features = ["derive", "color"] }
colored = "2.0"            # 彩色输出

# UUID和日志
uuid = { version = "1.0", features = ["v4", "serde"] }
log = "0.4"
env_logger = "0.10"

# 错误处理
anyhow = "1.0"
thiserror = "1.0"

# 前端依赖 (package.json)
"@tauri-apps/api": "^2.5.0"
"@tauri-apps/plugin-notification": "^2.1.0"
"@tauri-apps/plugin-shell": "^2.1.0"
"react": "^18.2.0"
"react-dom": "^18.2.0"
"lucide-react": "^0.344.0"
"tailwindcss": "^3.4.1"
"typescript": "^5.2.2"
"vite": "^5.1.4"
```

## 📚 Rust学习路径

### 第1周: 基础架构
**学习重点:**
- **所有权系统** - 理解借用和生命周期
- **错误处理** - Result和Option类型
- **结构体和枚举** - 数据建模
- **模块系统** - 代码组织

**实现目标:**
- 基本项目结构
- 数据模型定义
- 简单CLI界面
- 本地数据存储

### 第2周: 核心功能
**学习重点:**
- **特征(Traits)** - 接口设计
- **泛型** - 代码复用
- **集合类型** - Vec, HashMap等
- **时间处理** - chrono库使用

**实现目标:**
- 计时器核心逻辑
- 任务管理系统
- 数据库CRUD操作
- 基础统计功能

### 第3周: 前端开发和系统集成
**学习重点:**
- **Tauri架构** - 前后端通信
- **React开发** - 现代Web界面
- **TypeScript** - 类型安全
- **异步编程** - async/await

**实现目标:**
- React用户界面
- Tauri命令接口
- 实时数据同步
- 系统通知和托盘

### 第4周: 高级特性
**学习重点:**
- **宏编程** - 代码生成
- **unsafe代码** - 系统调用
- **性能优化** - 内存和CPU
- **测试** - 单元测试和集成测试

**实现目标:**
- 系统集成功能
- 性能优化
- 完整测试覆盖
- 打包和分发

## 🎨 用户界面设计

### CLI界面命令
```bash
# 基本操作
time-tracker start "编程学习" --category "学习"
time-tracker pause
time-tracker stop
time-tracker status

# 数据查询
time-tracker list --today
time-tracker stats --week
time-tracker report --month

# 配置管理
time-tracker config set pomodoro.work_duration 25
time-tracker category add "健身" --color "#FF5722"
```

### React Web界面设计
现代化的Tauri + React界面，支持：

**主要界面组件:**
- **仪表板 (Dashboard)**: 实时计时器、今日统计、效率评分
- **任务管理 (TaskManagement)**: 任务创建、编辑、分类
- **分类管理 (CategoryManagement)**: 分类配置、颜色主题
- **统计报告 (Statistics)**: 数据分析、图表展示、趋势分析
- **设置 (Settings)**: 应用配置、主题切换、通知设置
- **关于 (About)**: 应用信息、更新日志、帮助文档

**界面特性:**
- 响应式设计，支持多种屏幕尺寸
- 可调节侧边栏，支持折叠/展开
- 现代化Material Design风格
- 实时数据更新，无需手动刷新
- 系统托盘集成，支持后台运行

## 📊 数据模型设计

### 核心数据结构
```rust
// 任务记录
#[derive(Debug, Clone, Serialize, Deserialize)]
struct TimeEntry {
    id: u64,
    task_name: String,
    category_id: u64,
    start_time: DateTime<Local>,
    end_time: Option<DateTime<Local>>,
    duration: Duration,
    description: Option<String>,
    tags: Vec<String>,
}

// 任务分类
#[derive(Debug, Clone, Serialize, Deserialize)]
struct Category {
    id: u64,
    name: String,
    color: String,
    icon: Option<String>,
    target_hours_per_day: Option<f32>,
}

// 统计数据
#[derive(Debug, Clone, Serialize, Deserialize)]
struct TimeStats {
    date: NaiveDate,
    category_stats: HashMap<u64, Duration>,
    total_time: Duration,
    efficiency_score: f32,
}
```

## 🚀 开发里程碑

### 里程碑1: MVP版本 (第1-2周)
- ✅ 基本计时功能
- ✅ 数据本地存储
- ✅ 简单CLI界面
- ✅ 基础统计报告

**验收标准:**
- 能够开始/停止计时
- 数据持久化保存
- 查看今日/本周统计

### 里程碑2: 完整功能 (第3周)
- ✅ GUI界面
- ✅ 分类管理
- ✅ 番茄钟模式
- ✅ 系统通知

**验收标准:**
- 友好的图形界面
- 完整的任务分类
- 自动提醒功能

### 里程碑3: 生产就绪 (第4周)
- ✅ 系统集成
- ✅ 数据导出
- ✅ 性能优化
- ✅ 完整测试

**验收标准:**
- 系统托盘集成
- 数据备份恢复
- 流畅的用户体验

## 🔧 开发环境设置

### 1. 创建项目
```bash
cargo new time_tracker
cd time_tracker
```

### 2. 配置依赖
**Rust后端依赖 (Cargo.toml):**
```toml
[dependencies]
tauri = { version = "2.5.1", features = ["tray-icon"] }
tauri-plugin-shell = "2.2"
tauri-plugin-notification = "2.2"
rusqlite = { version = "0.29", features = ["bundled", "backup"] }
serde = { version = "1.0", features = ["derive"] }
chrono = { version = "0.4", features = ["serde"] }
tokio = { version = "1.0", features = ["full"] }
uuid = { version = "1.0", features = ["v4", "serde"] }
```

**前端依赖 (package.json):**
```json
{
  "dependencies": {
    "@tauri-apps/api": "^2.5.0",
    "react": "^18.2.0",
    "react-dom": "^18.2.0",
    "lucide-react": "^0.344.0",
    "tailwindcss": "^3.4.1"
  },
  "devDependencies": {
    "@tauri-apps/cli": "^2.5.0",
    "typescript": "^5.2.2",
    "vite": "^5.1.4"
  }
}
```

### 3. 初始化数据库
```sql
-- 创建数据库表
CREATE TABLE categories (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    name TEXT NOT NULL UNIQUE,
    color TEXT NOT NULL,
    icon TEXT,
    target_hours_per_day REAL
);

CREATE TABLE time_entries (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    task_name TEXT NOT NULL,
    category_id INTEGER NOT NULL,
    start_time TEXT NOT NULL,
    end_time TEXT,
    duration INTEGER NOT NULL,
    description TEXT,
    tags TEXT,
    FOREIGN KEY (category_id) REFERENCES categories (id)
);
```

## 📈 学习成果评估

### 技能掌握检查表
- [ ] **Rust基础语法** - 所有权、借用、生命周期
- [ ] **错误处理** - Result类型和错误传播
- [ ] **异步编程** - async/await和tokio
- [ ] **Tauri开发** - 桌面应用框架使用
- [ ] **React开发** - 现代Web界面开发
- [ ] **TypeScript** - 类型安全的前端开发
- [ ] **数据库操作** - SQLite和数据模型设计
- [ ] **IPC通信** - 前后端数据交互
- [ ] **系统集成** - 托盘、通知、文件操作
- [ ] **测试** - 单元测试和集成测试
- [ ] **项目管理** - Cargo和npm包管理

### 实际应用价值
- [ ] **日常使用** - 真正提高时间管理效率
- [ ] **数据洞察** - 了解自己的时间分配模式
- [ ] **习惯养成** - 培养良好的时间记录习惯
- [ ] **技能展示** - 作为技术能力的展示项目

## 🎯 下一步行动

1. **立即开始** - 创建项目并实现基本计时功能
2. **每日迭代** - 每天添加一个小功能
3. **实际使用** - 开发过程中就开始使用来追踪开发时间
4. **持续改进** - 根据使用体验不断优化

这个项目不仅能让你学会Rust，更重要的是能真正改善你的时间管理，提高工作效率！

---

**开始你的Rust时间追踪器开发之旅吧！** 🚀