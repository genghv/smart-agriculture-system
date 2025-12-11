# Smart Agriculture System

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python](https://img.shields.io/badge/Python-3.11+-blue.svg)](https://www.python.org/downloads/)
[![AI](https://img.shields.io/badge/AI-LLM%20集成-green.svg)](#ai决策编排)

一个集成AI决策、权限管理、数据加密和数据库系统的智能云平台，专为农业、生态等领域的数据分析与决策支持而设计。

## 📋 项目概述

Smart Agriculture System 是一个模块化的智能农业决策支持平台，通过AI编排器实现多专家并行推理，结合细粒度权限控制和安全的数据传输，为现代农业提供智能化的数据分析与决策支持。

**核心特色：**
- 🤖 **智能AI决策** - 多专家Agent并行推理与仲裁
- 🔒 **权限管理** - 基于RBAC的细粒度权限控制
- 🛡️ **安全加密** - 双层数据加密机制，分层密钥管理
- 📊 **数据库系统** - SQLite轻量级数据库，权限分离设计
- 🔧 **MCP架构** - 模型控制程序，实现大模型与本地程序无缝集成

## ✨ 主要功能

### 🔥 核心功能
- **AI决策编排**
  - 基于多专家Agent的并行推理与仲裁
  - 动态专家选择与任务分发
  - 工单生命周期管理
  - 决策日志记录与追踪

- **权限管理系统**
  - 基于角色的访问控制(RBAC)
  - 细粒度权限划分(读/写/管理)
  - 多级别资源保护
  - 表级权限分离设计

- **加密与安全**
  - 双层数据加密机制(对称加密+SigV4)
  - 分层密钥管理(Master Key、DEK、KEK)
  - JWT令牌管理与验证
  - CA证书管理与用户认证

- **数据库系统**
  - SQLite轻量级数据库
  - 高效的查询执行引擎
  - 数据完整性与一致性保障

- **MCP(模型控制程序)**
  - 工具注册与管理
  - 工具执行与参数验证
  - 权限沙箱控制
  - 提示词生成与优化

### 🤖 AI推理模式
系统支持两种AI推理模式：

1. **ReAct推理引擎**
   - 通过"思考-行动-观察"循环进行推理
   - 支持多步骤推理和策略调整
   - 适合复杂问题解决场景

2. **Function Schema推理引擎**
   - 基于函数调用的结构化输出推理
   - 直接生成工具调用请求
   - 支持多工具并行调用

## 🚀 快速开始

### 环境要求

- Python 3.11 或更高版本
- pip 包管理器

### 安装步骤

1. **克隆项目**
   ```bash
   git clone https://github.com/your-org/smart-agriculture-system.git
   cd smart-agriculture-system
   ```

2. **创建虚拟环境**
   ```bash
   python -m venv venv
   source venv/bin/activate  # Linux/Mac
   # 或 venv\Scripts\activate  # Windows
   ```

3. **安装依赖**
   ```bash
   pip install -r requirements.txt
   ```

4. **配置环境变量**
   ```bash
   cp .env.example .env
   # 编辑 .env 文件，填入必要的配置信息
   ```

5. **初始化数据库**
   ```bash
   python scripts/init_db.py
   ```

6. **运行应用**
   ```bash
   python main.py
   ```

### Docker部署

```bash
# 构建镜像
docker build -t smart-agriculture-system .

# 运行容器
docker run -p 8000:8000 smart-agriculture-system
```

## 📁 项目结构

```
smart-agriculture-system/
├── README.md                 # 项目说明文档
├── requirements.txt          # Python依赖列表
├── main.py                   # 应用入口文件
├── dockerfile               # Docker配置文件
├── .env.example             # 环境变量示例
│
├── src/                     # 源代码目录
│   ├── __init__.py
│   ├── core/                # 核心功能模块
│   │   ├── __init__.py
│   │   ├── ai/              # AI决策编排
│   │   │   ├── __init__.py
│   │   │   ├── llm.py       # LLM集成与推理引擎
│   │   │   └── agents/      # 专家Agent实现
│   │   ├── auth/            # 权限管理
│   │   │   ├── __init__.py
│   │   │   ├── rbac.py      # RBAC权限控制
│   │   │   └── jwt.py       # JWT认证
│   │   ├── crypto/          # 加密模块
│   │   │   ├── __init__.py
│   │   │   ├── encryption.py # 双层加密机制
│   │   │   └── key_manager.py # 分层密钥管理
│   │   ├── database/        # 数据库模块
│   │   │   ├── __init__.py
│   │   │   ├── manager.py   # 数据库管理器
│   │   │   └── models/      # 数据模型
│   │   └── mcp/             # 模型控制程序
│   │       ├── __init__.py
│   │       ├── tool_registry.py # 工具注册
│   │       └── executor.py     # 工具执行器
│   │
├── scripts/                 # 脚本文件
│   ├── init_db.py          # 数据库初始化
│   ├── setup.py            # 项目设置
│   └── demo.py             # 示例演示
│
├── tests/                   # 测试文件
│   ├── __init__.py
│   ├── test_ai/            # AI模块测试
│   ├── test_auth/          # 认证模块测试
│   ├── test_crypto/        # 加密模块测试
│   └── test_database/      # 数据库模块测试
│
├── docs/                    # 文档目录
│   ├── api/                # API文档
│   ├── deployment/         # 部署文档
│   └── architecture/       # 架构文档
│
└── data/                    # 数据目录
    ├── database/           # SQLite数据库文件
    ├── logs/               # 日志文件
    └── exports/            # 数据导出
```

## 🛠️ 技术栈

### 核心依赖
- **核心语言**: Python 3.11+
- **数据库**: SQLite
- **异步框架**: asyncio
- **加密库**: cryptography, boto3
- **LLM集成**: DeepSeek API
- **权限框架**: 自定义RBAC实现
- **认证**: JWT, SigV4
- **Web框架**: Flask/FastAPI (可选)

### 系统架构
```
┌─────────────────────────────────────────────────────────────┐
│                    应用层 (Application Layer)                │
│  ┌─────────────┐  ┌─────────────┐  ┌─────────────────────────┐ │
│  │  Web UI/API │  │  移动端接口  │  │  边缘设备通信接口         │ │
│  └──────┬──────┘  └──────┬──────┘  └──────────┬────────────────┘ │
└─────────┼────────────────┼────────────────────┼────────────────────┘
          │                │                    │
┌─────────▼────────────────▼────────────────────▼────────────────────┐
│                    业务逻辑层 (Service Layer)                    │
│  ┌─────────────┐  ┌─────────────┐  ┌─────────────────────────┐  │
│  │  AI编排器   │  │  权限管理器  │  │  工单服务                │  │
│  └──────┬──────┘  └──────┬──────┘  └──────────┬────────────────┘  │
└─────────┼────────────────┼────────────────────┼────────────────────┘
          │                │                    │
┌─────────▼────────────────▼────────────────────▼────────────────────┐
│                    数据访问层 (Data Access Layer)                 │
│  ┌─────────────┐  ┌─────────────┐  ┌─────────────────────────┐  │
│  │  LLM客户端  │  │  MCP中间层   │  │  数据库管理器            │  │
│  │  (带加密)   │  │(工具注册/执行)│  │  (权限分离)            │  │
│  └──────┬──────┘  └──────┬──────┘  └──────────┬────────────────┘  │
└─────────┼────────────────┼────────────────────┼────────────────────┘
          │                │                    │
┌─────────▼────────────────▼────────────────────▼────────────────────┐
│                 基础设施层 (Infrastructure Layer)                 │
│  ┌─────────────┐  ┌─────────────┐  ┌─────────────────────────┐  │
│  │  LLM服务    │  │  加密模块    │  │  SQLite数据库           │  │
│  │ (DeepSeek)  │  │ (分层密钥)   │  │ (多表权限分离)          │  │
│  │ 本地模型    │  │             │  │                        │  │
│  └─────────────┘  └─────────────┘  └─────────────────────────┘  │
└─────────────────────────────────────────────────────────────────┘
```

## 🔧 开发指南

### 本地开发环境搭建

1. **设置开发环境**
   ```bash
   # 安装开发依赖
   pip install -r requirements-dev.txt
   
   # 安装预提交钩子
   pre-commit install
   
   # 运行测试
   pytest tests/
   ```

2. **代码规范**
   - 遵循 [PEP 8](https://pep8.org/) 风格指南
   - 使用 [Black](https://black.readthedocs.io/) 代码格式化
   - 使用 [mypy](https://mypy.readthedocs.io/) 类型检查
   - 添加适当的文档字符串

3. **提交规范**
   ```bash
   # 功能提交
   git commit -m "feat: 添加新的AI推理模式"
   
   # 修复提交
   git commit -m "fix: 修复权限验证漏洞"
   
   # 文档提交
   git commit -m "docs: 更新API文档"
   ```

### API使用示例

```python
from src.core.ai import LLMManager
from src.core.auth import RBACManager

# 初始化AI管理器
llm_manager = LLMManager()

# 创建AI任务
task = {
    "type": "crop_prediction",
    "data": {
        "soil_type": "clay",
        "temperature": 25,
        "humidity": 60
    },
    "agent_mode": "react"  # 或 "function"
}

# 执行AI决策
result = llm_manager.execute_task(task)
print(result)
```

## 📖 使用文档

- [API文档](docs/api/README.md)
- [部署指南](docs/deployment/README.md)
- [架构设计](docs/architecture/README.md)
- [安全指南](docs/security/README.md)

## 🤝 贡献指南

我们欢迎所有形式的贡献！请阅读 [贡献指南](CONTRIBUTING.md) 了解详情。

### 贡献流程

1. **Fork** 本仓库
2. **创建** 特性分支 (`git checkout -b feature/AmazingFeature`)
3. **提交** 更改 (`git commit -m 'Add some AmazingFeature'`)
4. **推送** 到分支 (`git push origin feature/AmazingFeature`)
5. 创建 **Pull Request**

### 问题反馈

- 使用 [GitHub Issues](https://github.com/your-org/smart-agriculture-system/issues) 提交问题
- 提供详细的错误信息和复现步骤
- 标签分类: BUG / FEATURE / DOCUMENTATION

## 📝 更新日志

### [1.0.0] - 2024-12-11
- 🎉 初始版本发布
- ✨ 实现AI决策编排功能
- 🔒 添加权限管理系统
- 🛡️ 实现双层加密机制
- 📊 集成SQLite数据库系统

## 📄 许可证

本项目采用 [MIT 许可证](LICENSE)。

## 📞 联系方式

- 项目维护者: [Your Name](mailto:gengxberww@petalmail.com)
- 项目主页: [https://github.com/your-org/smart-agriculture-system](https://github.com/your-org/smart-agriculture-system)

## 🙏 致谢

感谢所有为本项目做出贡献的开发者和研究人员！

---

**让现代农业更智能，让决策更科学！** 🌱🤖