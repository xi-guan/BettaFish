# 🛠️ BettaFish 技术栈详解

## 概述

BettaFish（微舆）是一个基于 Python 的多智能体舆情分析系统，采用模块化架构设计，集成了现代化的 Web 框架、机器学习模型、分布式爬虫和多智能体协作系统。

---

## 核心技术栈

### 1. 编程语言
- **Python 3.11+**: 主要开发语言，利用其丰富的生态系统和异步编程能力

### 2. Web 框架与服务

#### 后端框架
- **Flask 2.3.3**: 主应用框架，提供 RESTful API 和服务编排
- **Flask-SocketIO 5.3.6**: 实现实时双向通信，用于前端状态更新
- **FastAPI 0.110.2**: 高性能异步 API 框架
- **Uvicorn 0.29.0**: ASGI 服务器，支持异步请求处理

#### 前端框架
- **Streamlit 1.28.1**: 快速构建数据应用界面，为各个 Agent 提供独立的交互界面
  - QueryEngine (端口 8503)
  - MediaEngine (端口 8502)
  - InsightEngine (端口 8501)
  - Flask 主应用 (端口 5000)

#### 实时通信
- **python-socketio 5.8.0**: WebSocket 协议支持
- **eventlet 0.33.3**: 并发网络库，支持异步事件处理

---

### 3. 大语言模型 (LLM) 集成

#### LLM 接口
- **OpenAI SDK (>=1.3.0)**: 统一的 LLM 调用接口，支持 OpenAI 兼容的所有模型
  - Insight Agent LLM
  - Media Agent LLM
  - Query Agent LLM
  - Report Agent LLM
  - Forum Host LLM
  - Keyword Optimizer LLM

#### 多模态能力
- 支持文本、图像、视频等多模态内容分析
- 集成视频理解和结构化信息提取能力

---

### 4. 数据存储与管理

#### 关系型数据库
- **PostgreSQL 15**: 主要数据库（Docker 部署推荐）
- **MySQL**: 可选数据库支持
- **SQLAlchemy 2.0.35**: ORM 框架，提供数据库抽象层
- **asyncpg 0.29.0**: PostgreSQL 异步驱动
- **pymysql 1.1.0**: MySQL 同步驱动
- **aiomysql 0.2.0 / asyncmy 0.2.9**: MySQL 异步驱动

#### 缓存与消息队列
- **Redis (>=4.6.0)**: 缓存存储、消息队列、Agent 间通信

#### 轻量级数据库
- **aiosqlite 0.21.0**: SQLite 异步支持

---

### 5. 网络爬虫技术栈

#### 浏览器自动化
- **Playwright 1.45.0**: 现代化浏览器自动化框架，支持：
  - 动态网页渲染
  - JavaScript 执行
  - 反爬虫绕过
  - 多平台支持（微博、小红书、抖音、快手等）

#### HTTP 客户端
- **requests 2.31.0**: 同步 HTTP 请求
- **httpx 0.28.1**: 异步 HTTP 客户端
- **aiohttp (>=3.8.0)**: 异步 HTTP 请求库

#### 页面解析
- **BeautifulSoup4 (>=4.12.0)**: HTML/XML 解析
- **lxml (>=4.9.0)**: 高性能 XML/HTML 解析器
- **parsel 1.9.1**: XPath/CSS 选择器支持
- **pyexecjs 1.5.1**: JavaScript 代码执行

---

### 6. 数据处理与分析

#### 数据处理
- **Pandas (>=2.0.0)**: 数据清洗、转换和分析
- **NumPy (>=1.24.0)**: 数值计算
- **regex (>=2023.8.8)**: 高级正则表达式

#### 中文文本处理
- **jieba 0.42.1**: 中文分词工具

#### 异步 I/O
- **aiofiles 23.2.1**: 异步文件操作

---

### 7. 机器学习与深度学习

#### 深度学习框架
- **PyTorch (>=2.0.0)**: 深度学习框架（支持 CPU/GPU）
- **Transformers (>=4.30.0)**: Hugging Face 模型库，支持：
  - BERT 系列模型
  - GPT-2 微调模型
  - Qwen 系列模型
  - 多语言情感分析模型

#### 传统机器学习
- **scikit-learn (>=1.3.0)**: 机器学习算法库
- **XGBoost (>=2.0.0)**: 梯度提升框架

#### 情感分析模型
1. **WeiboMultilingualSentiment**: 多语言情感分析（推荐）
2. **WeiboSentiment_Finetuned**: 微调 BERT/GPT-2 模型
3. **WeiboSentiment_SmallQwen**: 小参数 Qwen3 微调
4. **WeiboSentiment_MachineLearning**: 传统机器学习方法

---

### 8. 数据可视化

- **Plotly (>=5.17.0)**: 交互式图表
- **Matplotlib 3.9.0**: 静态图表
- **WordCloud 1.9.3**: 词云生成

---

### 9. 图像与视频处理

- **Pillow 9.5.0**: 图像处理库
- **OpenCV-Python (>=4.8.0)**: 计算机视觉库
- **FFmpeg**: 视频处理（系统依赖）

---

### 10. 搜索与信息检索

#### 搜索 API
- **Tavily Python (>=0.3.0)**: AI 搜索 API，用于 Query Agent
- **Bocha Web Search API**: 可选的网页搜索服务

---

### 11. 工具库与辅助功能

#### 配置管理
- **python-dotenv (>=1.0.0)**: 环境变量管理
- **Pydantic 2.5.2**: 数据验证和配置管理
- **pydantic-settings 2.2.1**: 设置管理

#### 日志与监控
- **Loguru (>=0.7.0)**: 现代化日志库，支持彩色输出和灵活配置

#### 重试与容错
- **Tenacity 8.2.2**: 重试机制库
- 自定义 retry_helper: 网络请求重试工具

#### 时间处理
- **python-dateutil (>=2.8.2)**: 日期时间解析
- **pytz (>=2023.3)**: 时区处理

#### 进度显示
- **tqdm (>=4.65.0)**: 进度条显示

---

### 12. 开发与测试工具

- **pytest (>=7.4.0)**: 单元测试框架
- **black (>=23.0.0)**: 代码格式化工具
- **flake8 (>=6.0.0)**: 代码质量检查

---

## 容器化与部署

### Docker 技术栈

#### 基础镜像
- **python:3.11-slim**: 轻量级 Python 基础镜像

#### 容器编排
- **Docker Compose 3.9**: 多容器应用编排
  - bettafish 服务（主应用）
  - PostgreSQL 15 数据库服务

#### 系统依赖
```dockerfile
- build-essential: 编译工具
- git: 版本控制
- libgl1, libglib2.0-0: OpenCV 依赖
- GTK/Pango/ATK 库: Playwright 浏览器依赖
- libxcb, libxcomposite: X11 依赖
- libnss3: 网络安全服务
- ffmpeg: 视频处理
```

#### 包管理器
- **uv**: 快速 Python 包安装工具

---

## 系统架构特性

### 1. 多智能体架构

#### Agent 类型
- **Query Agent**: 国内外新闻搜索，使用 Tavily API
- **Media Agent**: 多模态内容分析（短视频、图文）
- **Insight Agent**: 私有数据库深度挖掘
- **Report Agent**: 智能报告生成

#### Agent 协作机制
- **ForumEngine**: 论坛式多 Agent 协作
  - 论坛主持人 LLM 模型
  - Agent 间消息通信（forum_reader）
  - 多轮讨论与决策

### 2. 分布式爬虫系统 (MindSpider)

#### 模块组成
- **BroadTopicExtraction**: 话题提取模块
  - 今日新闻获取
  - 热点话题提取
  - 数据库管理

- **DeepSentimentCrawling**: 深度舆情爬取
  - 关键词管理
  - 多平台爬虫（微博、小红书、抖音、快手）
  - MediaCrawler 核心引擎

### 3. 数据库设计
- 模块化表结构设计（mindspider_tables.sql）
- 支持高并发读写
- 异步数据库操作

### 4. 异步编程模型
- 使用 asyncio 实现高并发
- 异步数据库访问（asyncpg, aiomysql）
- 异步 HTTP 请求（aiohttp, httpx）
- 异步文件 I/O（aiofiles）

---

## API 集成

### 第三方服务
- OpenAI 兼容 API（支持多家 LLM 供应商）
- Tavily Search API
- Bocha Web Search API（可选）

### 推荐 LLM API 供应商
- AIHubMix（推理时代）
- 302.AI
- VibeCodingAPI
- CodeCodex

---

## 项目特色技术

### 1. 轻量化设计
- 纯 Python 模块化实现
- 一键式 Docker 部署
- 清晰的代码结构

### 2. 高扩展性
- 插件化 Agent 工具集
- 自定义 LLM 模型支持
- 可定制报告模板
- 支持接入私有数据库

### 3. 多模态处理
- 图文内容分析
- 短视频内容提取
- 结构化信息卡片解析

### 4. 智能协作
- 论坛式 Agent 讨论机制
- 链式思维碰撞
- 集体智能决策

### 5. 容错机制
- 网络请求重试
- 异常处理与日志记录
- 优雅降级

---

## 性能优化

### 1. 并发处理
- 多 Agent 并行工作
- 异步任务执行
- 数据库连接池

### 2. 缓存策略
- Redis 缓存热点数据
- LLM 响应缓存
- 搜索结果缓存

### 3. 资源管理
- GPU/CPU 自适应
- 内存优化
- 浏览器资源复用

---

## 安全特性

### 1. 数据安全
- 环境变量管理（.env）
- 数据库连接加密
- API 密钥保护

### 2. 爬虫合规
- robots.txt 协议遵守
- 请求频率限制
- User-Agent 管理

---

## 技术栈总结

BettaFish 项目充分利用了现代 Python 生态系统的优势，通过：
- **模块化设计**实现了系统的高可维护性
- **异步编程**提升了系统的并发处理能力
- **容器化部署**简化了部署和运维流程
- **多智能体架构**提供了灵活的扩展能力
- **丰富的 ML/DL 工具**保证了分析的准确性

这使得 BettaFish 不仅是一个舆情分析系统，更是一个通用的数据分析引擎框架。
