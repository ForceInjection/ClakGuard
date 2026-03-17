# ClawGuard

🦞 AI Agent Skill 安全扫描平台

[![Status](https://img.shields.io/badge/status-design%20phase-blue)](docs/clawguard-design-document.md)
[![License](https://img.shields.io/badge/license-MIT-green)](LICENSE)

---

## 📋 项目概述

**ClawGuard** 是一个面向 AI Agent Skill 生态的安全扫描平台，用于检测用户上传的 Skill 包中的恶意行为。其核心理念是 **「用 Skill 检测 Skill」**——通过加载安全检测类 Skill 来分析目标 Skill 包，实现可扩展的安全扫描能力。

### 核心价值主张

| 方面        | 价值                                   |
| ----------- | -------------------------------------- |
| 🛡️ 安全防护 | 拦截恶意 Skill，保护用户数据和系统安全 |
| 🌱 生态健康 | 提升 Skill 市场的可信度和用户信任      |
| ✅ 合规要求 | 满足企业对第三方组件的安全审查需求     |
| ⚡ 开发效率 | 自动化扫描替代人工审计，加速发布流程   |

---

## 🚧 当前状态

> **⚠️ 设计讨论阶段**
>
> 本项目目前处于 **设计和讨论阶段**。我们正在就架构、威胁模型和实施方法收集社区反馈。

### 已完成

- ✅ 完整的设计文档（包含需求分析和系统架构）
- ✅ 基于 352+ 已知恶意样本的威胁建模
- ✅ 覆盖提示词注入、数据外泄、凭据窃取等的安全 Skill 目录
- ✅ CLI、API、CI/CD 和运行时网关集成模式

### 下一步计划

- 🔲 实现 MVP 版本（v0.1），包含核心安全检测 Skill
- 🔲 构建扫描引擎参考实现
- 🔲 基于 openclaw-malicious-skills 数据集建立检测效果基准
- 🔲 制定社区贡献安全检测 Skill 的指南

---

## 📚 文档

### 核心文档

| 文档                                                                            | 说明                      | 状态         |
| ------------------------------------------------------------------------------- | ------------------------- | ------------ |
| [设计文档](docs/clawguard-design-document.md)                                   | 完整需求分析与系统设计    | ✅ v1.0 草案 |
| [威胁模型](docs/clawguard-design-document.md#22-威胁模型)                       | 攻击向量、目标与阶段分析  | ✅ 已包含    |
| [安全 Skill 目录](docs/clawguard-design-document.md#5-内置-security-skill-设计) | 12 个检测 Skill 规划      | ✅ 已设计    |
| [接入指南](docs/clawguard-design-document.md#6-接入方式)                        | CLI、API、CI/CD、网关集成 | ✅ 已设计    |

### 关键章节

- [架构设计](docs/clawguard-design-document.md#41-架构概述) - 「Skill 检测 Skill」可扩展架构
- [检测流程](docs/clawguard-design-document.md#42-检测流程设计) - 5 阶段检测管道
- [风险模型](docs/clawguard-design-document.md#44-风险模型设计) - 评分、等级与可利用性评估
- [测试策略](docs/clawguard-design-document.md#7-测试策略) - 检出率>99%，误报率<5%

---

## 🏗️ 架构亮点

### 检测阶段

```text
阶段1: 包解析 → 阶段2: 元数据检查 → 阶段3: 静态分析 → 阶段4: 语义分析 → 阶段5: 沙箱执行 → 风险报告
```

### MVP 内置检测能力（v0.1）

- ✅ 提示词注入检测（R1）
- ✅ 数据外泄扫描（R2）
- ✅ 凭据窃取检测（R2）
- ✅ 远程代码执行检测（R3）
- ✅ 名称仿冒检测（R5）

### 风险类别

| 代号 | 类别         | 说明                     |
| ---- | ------------ | ------------------------ |
| R1   | 提示词注入   | Skill 描述中的恶意提示词 |
| R2   | 数据外泄     | 凭据/钱包窃取            |
| R3   | 远程代码执行 | 下载并执行远程恶意载荷   |
| R4   | 供应链攻击   | 依赖投毒、隐写术         |
| R5   | 隐藏行为     | 代码混淆、持久化污染     |

---

## 🤝 参与讨论

本项目处于设计阶段，欢迎反馈：

- 📖 阅读 [设计文档](docs/clawguard-design-document.md)
- 💬 就威胁模型、检测规则、集成模式提出建议
- 📝 分享 AI Agent 安全方面的经验

---

## 📊 设计目标

| 指标               | 目标值   |
| ------------------ | -------- |
| 检出率（已知样本） | >99%     |
| 误报率             | <5%      |
| 标准模式扫描延迟   | <10s     |
| 并发扫描能力       | >100 QPS |

---

## 🔗 参考资料

- [openclaw-malicious-skills](https://github.com/PiedPiper0709/openclaw-malicious-skills) - 352+ 恶意样本库
- [GuardDog](https://github.com/DataDog/guarddog) - PyPI/npm 恶意包检测
- [ClawSec](https://github.com/prompt-security/clawsec) - 运行时安全套件（互补）

---

## 📄 许可证

MIT License - 详见 [LICENSE](LICENSE) 文件

---

**最后更新**: 2026 年 3 月 17 日 | **设计版本**: v1.0 草案
