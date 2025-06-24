# TimeTracker - 时间追踪应用程序

一个功能完整的时间追踪应用程序，使用Rust开发，提供CLI和GUI两种界面模式。

## 功能特性

### 核心功能
- ⏱️ **时间记录**: 精确记录任务时间，支持开始/暂停/停止操作
- 📊 **统计分析**: 多维度数据统计和可视化图表
- 🏷️ **分类管理**: 灵活的任务分类系统
- 📝 **任务管理**: 完整的任务生命周期管理
- 🔍 **数据查询**: 强大的搜索和过滤功能

### 界面模式
- 🖥️ **图形界面(GUI)**: 基于egui的现代化界面
- 💻 **命令行界面(CLI)**: 高效的命令行操作

### 数据管理
- 💾 **本地存储**: 基于SQLite的可靠数据存储
- 📤 **数据导出**: 支持JSON、CSV、XML、HTML、Markdown格式
- 📥 **数据导入**: 支持多种格式的数据导入
- 🔄 **自动备份**: 可配置的自动备份功能

### 高级功能
- 🎨 **主题定制**: 多种主题和深色模式支持
- 🔔 **通知系统**: 桌面通知和声音提醒
- ⌨️ **快捷键**: 全局快捷键支持
- 🌍 **多语言**: 支持中文、英文、日文
- ⚙️ **配置管理**: 丰富的配置选项

## 文件存储

### 开发环境
在开发环境中（使用 `cargo run`），所有配置和数据文件都存储在项目根目录的 `data/` 文件夹中：

```
time-tracker/
├── data/
│   ├── config/
│   │   ├── theme.json      # 主题配置
│   │   └── config.toml     # 应用配置
│   ├── logs/               # 日志文件
│   ├── backups/            # 数据库备份
│   ├── exports/            # 导出数据
│   └── timetracker.db      # SQLite 数据库
└── (其他项目文件)
```

### 生产环境
在生产环境中，文件存储在操作系统的标准位置：

- **Windows**: `%APPDATA%\TimeTracker\`
- **macOS**: `~/Library/Application Support/timetracker/`  
- **Linux**: `~/.local/share/timetracker/`

### 配置文件管理
- 主题配置会自动保存和加载
- 设置页面显示实际的配置文件路径
- 开发时所有文件都在项目内，不会污染系统目录

## 主题系统

TimeTracker 支持灵活的主题配置：

### 主题模式
- **浅色主题** - 适合日间使用
- **深色主题** - 适合夜间使用  
- **跟随系统** - 自动根据操作系统设置切换明暗模式

### 系统主题检测
应用程序会自动检测以下系统的主题设置：
- **Windows** - 检测系统设置中的应用主题偏好
- **macOS** - 检测系统偏好设置中的外观模式
- **Linux** - 支持GNOME和KDE桌面环境的主题检测

### 使用方法
1. 在设置页面的外观选项中选择"跟随系统"
2. 或在菜单栏 > 视图 > 主题 中选择对应模式
3. 系统主题变化时会自动切换并显示通知

## 安装说明

### 系统要求
- Windows 10/11, macOS 10.15+, 或 Linux
- Rust 1.70+ (如果从源码编译)

### 从源码编译

```bash
# 克隆仓库
git clone https://github.com/username/time-tracker.git
cd time-tracker

# 编译项目
cargo build --release

# 运行应用程序
cargo run --release
```

## 使用指南

### GUI模式

启动GUI界面：
```bash
cargo run --release
# 或
./time-tracker
```

### CLI模式

查看帮助信息：
```bash
cargo run --release -- --help
```

常用CLI命令：
```bash
# 开始计时
cargo run --release -- start "工作任务" --category "工作"

# 停止计时
cargo run --release -- stop

# 查看今日统计
cargo run --release -- stats --today

# 列出所有分类
cargo run --release -- categories list

# 导出数据
cargo run --release -- export --format json --output data.json
```

## 项目结构

```
src/
├── main.rs              # 主程序入口
├── lib.rs               # 库入口
├── models/              # 数据模型
├── database/            # 数据库层
├── cli/                 # CLI界面
├── gui/                 # GUI界面
├── utils/               # 工具函数
├── config/              # 配置管理
└── errors.rs            # 错误处理
```

## 开发

```bash
# 运行测试
cargo test

# 格式化代码
cargo fmt

# 检查代码质量
cargo clippy
```

## 📖 使用指南

### CLI命令
```bash
# 开始计时
time-tracker start "学习Rust" --category "编程"

# 暂停计时
time-tracker pause

# 停止计时
time-tracker stop

# 查看状态
time-tracker status

# 查看统计
time-tracker stats --today
time-tracker stats --week
```

### GUI操作
1. 启动应用后，在任务名称框输入当前任务
2. 选择或创建任务分类
3. 点击"开始"按钮开始计时
4. 使用"暂停"和"停止"控制计时状态
5. 在统计页面查看时间分析

## 🏗️ 项目架构

```
src/
├── main.rs              # 程序入口
├── lib.rs               # 库文件
├── cli/                 # 命令行界面
├── gui/                 # 图形界面
├── core/                # 核心业务逻辑
├── storage/             # 数据存储层
└── utils/               # 工具函数
```

## 🛠️ 技术栈

- **语言**: Rust 2021 Edition
- **GUI框架**: egui + eframe
- **数据库**: SQLite (rusqlite)
- **异步运行时**: Tokio
- **CLI框架**: clap
- **时间处理**: chrono
- **序列化**: serde

## 📊 学习价值

这个项目涵盖了Rust开发的核心概念：
- 所有权系统和借用检查
- 错误处理 (Result/Option)
- 异步编程 (async/await)
- 特征和泛型
- 模块系统
- GUI开发
- 数据库操作
- 系统编程

## 🤝 贡献指南

1. Fork 项目
2. 创建功能分支 (`git checkout -b feature/AmazingFeature`)
3. 提交更改 (`git commit -m 'Add some AmazingFeature'`)
4. 推送到分支 (`git push origin feature/AmazingFeature`)
5. 打开 Pull Request

## 📄 许可证

本项目采用 MIT 许可证 - 查看 [LICENSE](LICENSE) 文件了解详情。

## 🎯 开发路线图

- [x] 基础项目结构
- [ ] 核心计时功能
- [ ] 数据库集成
- [ ] CLI界面
- [ ] GUI界面
- [ ] 统计分析
- [ ] 系统集成
- [ ] 数据导出
- [ ] 性能优化

---

**开始你的时间管理之旅！** ⏰