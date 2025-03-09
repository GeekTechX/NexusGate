<div align="center">
<img src="./assets/img/banner-cn.png" />
<h1>NexusGate</h1>
仅需一行代码，完成 Agent 应用的监控与管理

[![GitHub license](https://img.shields.io/github/license/geekchange/nexusgate)](https://github.com/geekchange/nexusgate/blob/main/LICENSE)
[![Docker Pulls](https://img.shields.io/docker/pulls/geekchange/nexusgate)](https://hub.docker.com/r/geekchange/nexusgate)
[![GitHub stars](https://img.shields.io/github/stars/geekchange/nexusgate)](https://github.com/geekchange/nexusgate/stargazers)
[![GitHub issues](https://img.shields.io/github/issues/geekchange/nexusgate)](https://github.com/geekchange/nexusgate/issues)
[![Free Use](https://img.shields.io/badge/free-pricing?logo=free&color=%20%23155EEF&label=pricing&labelColor=%20%23528bff)](https://img.shields.io/badge/free-pricing?logo=free&color=%20%23155EEF&label=pricing&labelColor=%20%23528bff)
</div>

<div align="right">
  <a href="CONTRIBUTING.md">English</a>
</div>

- [🚀 简介](#-简介)
- [🌟 主要特点](#-主要特点)
- [🚀 快速启动](#-快速启动)
- [🔍 系统功能](#-系统功能)
- [👨‍💻 面向开发者](#-面向开发者)
- [👨‍💼 面向管理员](#-面向管理员)
- [🗺️ 发展路线图](#-发展路线图)

---

## 🚀 简介

NexusGate 是一个 Agent 应用监控和管理平台。它将帮助 Agent 应用了解用户反馈情况而无需额外开发，加速 Agent 优化迭代的生命周期。

使用 NexusGate，您只需修改一行代码即可监控、管理和优化您的 Agent 应用。它还能帮助企业通过开箱即用、一键设置建立内部智能基座。

## ✨ 主要特点

- **全面的 LLM 管理**：通过统一管理系统专注于您的 AI 应用，提高质量、降低成本、减少延迟并确保安全。兼容所有主流大型语言模型服务和推理框架。

- **评估和迭代**：利用强大的工具和洞察分析、修改和迭代下游 LLM 应用。

- **生产监控**：记录所有生产交互以进行监控、分析、调试、优化。

- **企业级管理**：一键管理下游应用，提供 LLM 内容的计量和审计。

## 🐳 快速启动

NexusGate 提供 Docker 镜像，支持 ARM 和 x86 架构。

```bash
# 拉取最新镜像
docker pull geekchange/nexusgate:latest

# 使用默认配置运行
docker run -d -p 3000:3000 -p 8000:8000 \
  --name nexusgate \
  -v nexusgate-data:/app/data \
  geekchange/nexusgate:latest

# 访问仪表板
# 在浏览器中打开 http://localhost:3000
```

高级配置：

```bash
# 使用环境变量运行
docker run -d -p 3000:3000 -p 8000:8000 \
  --name nexusgate \
  -v nexusgate-data:/app/data \
  -e DATABASE_URL="postgresql://user:password@host:port/dbname" \
  -e AUTH_SECRET="your-secret-key" \
  geekchange/nexusgate:latest
```

## 🔍 系统功能

### 1. 上游管理

连接和管理多个 LLM 提供商，包括企业大模型一体机或公共模型服务提供商（DeepSeek、阿里千问等）。

![创建上游配置](./assets/img/upstream-config.png)

NexusGate 支持 20 多个经过测试的上游服务和部署框架，同时支持多个下游应用，为您提供灵活性和选择。

### 2. 全面日志记录

监控所有交互的详细信息，包括请求时间戳、状态、输入提示、生成内容、模型信息、Token 使用情况、延迟指标和用户反馈。

![带有对话详情侧边栏的历史记录](./assets/img/history-log-details.png)

系统提供所有 API 密钥聊天记录的管理员视图和特定 API 密钥的历史记录，并带有请求细节和对话上下文的详细侧边栏视图。

![历史记录显示](./assets/img/history-table.png)

### 3. 应用管理

通过 API 密钥创建和管理、用户友好的命名约定、过期设置和可见性控制来控制和配置下游应用。

![创建带有 API 密钥设置的应用](./assets/img/create-application.png)

## 👨‍💻 面向开发者

### 一行代码集成

只需修改一行代码即可将 NexusGate 集成到您现有的 LLM 应用中：

#### Python (使用 OpenAI 库)

```python
# 修改前:
from openai import OpenAI
client = OpenAI(api_key="your-openai-api-key")

# 修改后:
from openai import OpenAI
client = OpenAI(api_key="your-nexusgate-api-key", base_url="https://your-nexusgate-server/v1")
```

#### JavaScript/TypeScript

```javascript
// 修改前:
import OpenAI from 'openai';
const openai = new OpenAI({ apiKey: 'your-openai-api-key' });

// 修改后:
import OpenAI from 'openai';
const openai = new OpenAI({ 
  apiKey: 'your-nexusgate-api-key',
  baseURL: 'https://your-nexusgate-server/v1'
});
```

### API 文档

NexusGate 提供全面的 OpenAPI 文档，便于与您现有的系统和工作流程集成。可以通过以下地址访问 OpenAPI 规范：

```
https://your-nexusgate-server/api/docs
```

该文档包括所有可用端点、请求/响应格式和身份验证要求，使开发者能够快速理解并利用 NexusGate 的全部功能。

## 👨‍💼 面向管理员

### 集中式 LLM 管理

NexusGate 为管理组织所有 LLM 应用提供统一仪表板：

- **成本控制**：跟踪所有应用和提供商的 Token 使用情况
- **安全监督**：监控所有提示和完成内容，确保合规和数据保护
- **性能优化**：识别瓶颈并优化响应时间
- **使用分析**：了解不同团队和应用如何利用 LLM 资源

### 应用管理

控制和配置下游应用，提供增强安全性的灵活过期设置、控制成本的速率限制和使用限制，以及针对不同模型和功能的精细权限设置。

## 🗺️ 发展路线图

我们不断为 NexusGate 添加新功能和能力。以下是我们接下来的工作计划：

- [ ] 🌐 国际化：完成 i18n 支持，提供官方中文支持。
- [ ] 📊 增强分析：扩展我们的监控指标，包括成功率、请求量、Token 使用统计、请求完成率、Agent 使用量排行、模型使用量排行、错误分析、全链路延迟、推理延迟和吞吐量等测量。
- [ ] 🔄 Prometheus 集成：通过与外部 Prometheus 实例集成，监控服务器硬件、推理框架和其他信息源，创建全面的概览仪表板。
- [ ] 🚦 流量控制 ：为每个 API 密钥实现精细的流量管理，包括特定模型的配额和优先级，使管理员能够精确控制资源分配。
- [ ] 💡 手动上报 SDK：开发用于更精细跟踪的 SDK，可直接嵌入开发者代码，实现更详细的监控，如终端用户分析。
- [ ] 👍 反馈系统：构建强大的反馈机制，收集和分析用户对 AI 生成内容的响应。
- [ ] 💬 提示词管理：创建用于提示词创建、优化和批量测试的工具，帮助开发者制作与 LLM 更有效的交互。
  - [ ] 🧠 自动化评估：利用 LLM 自动评估输出并提供质量指标，无需人工干预。
  - [ ] 📚 数据集创建和微调：实现数据集管理和模型微调流水线，一键导入 [LLaMa Factory](https://github.com/hiyouga/LLaMA-Factory) 微调，并使用 [SwanLab](https://github.com/SwanHubX/SwanLab) 监控。
- [ ] 🛠️ 工具集成：通过在网关层实现功能并通过标准 API 接口暴露，为没有内置工具（如网络搜索）的模型添加功能。

## 📝 许可证

[Apache License 2.0](LICENSE)

## 🤝 贡献

我们欢迎各种技能水平的开发者贡献！无论是修复错误、添加功能还是改进文档，您的投入都很有价值。

请查看 [CONTRIBUTING.md](CONTRIBUTING.md) 了解如何开始。

**Contributors**

<img src="https://contrib.rocks/image?repo=GeekChange/NexusGate" />

## 📚 文档

有关更详细的信息，请访问我们的[官方文档](https://docs.nexusgate.io)。