# ✈️ Vibe Traveling — Universal AI Travel Planner

> **一句话 → 完整旅行方案 | One sentence → Complete travel plan**
>
> 默认中文，English supported. 适配 Claude / ChatGPT / Gemini / DeepSeek / 任意 LLM Agent.

[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](./LICENSE)
[![Platform](https://img.shields.io/badge/Platform-Any%20LLM-blue)]()
[![Author](https://img.shields.io/badge/Author-BrightyLudwig-orange)](https://github.com/BrightyLudwig)

---

## 📖 这是什么 / What

**Vibe Traveling** 是一个通用的 AI 旅行规划系统提示词。告诉 AI 你的旅行想法——去哪儿、几天、和谁、喜欢什么——AI 会生成一份可直接执行的逐日行程。

不是"旅行搜索"，是"旅行创作"。零泛化，每个推荐都是真实具体的地名、餐厅、拍照机位。

---

## 🚀 使用方式 / How to Use

### Claude Code（一键安装）

```bash
claude plugins install BrightyLudwig/vibe-traveling
```

安装后输入 `/vibe-traveling` 即可。

### ChatGPT / GPTs

创建 Custom GPT → 将 [`PROMPT.md`](./PROMPT.md) 内容粘贴到 Instructions 中。

### Claude / Anthropic API

将 [`PROMPT.md`](./PROMPT.md) 内容作为 system prompt 使用。

### Gemini / Google AI Studio

将 [`PROMPT.md`](./PROMPT.md) 内容粘贴到 System Instructions 中。

### DeepSeek / 其他 LLM

将 [`PROMPT.md`](./PROMPT.md) 内容作为 system message 传入 API。

### Cursor / Windsurf / Copilot

将 [`PROMPT.md`](./PROMPT.md) 内容添加到项目规则文件（`.cursorrules` / `.windsurfrules` / `.github/copilot-instructions.md`）中。

---

## 📂 文件说明 / Files

| 文件 | 用途 |
|------|------|
| `SKILL.md` | Claude Code skill 定义（含平台 frontmatter） |
| `PROMPT.md` | 通用系统提示词（无平台依赖，可粘贴到任意 Agent） |
| `README.md` | 项目说明 |

---

## 💡 使用示例 / Usage Examples

```
帮我规划一次去云南的旅行，7天，喜欢自然风光和美食，预算中等

东京4天京都2天，喜欢拉面和拍照，中等预算

把第三天放慢一点，增加一个博物馆

换成美食版
```

---

## 🧠 能力 / Capabilities

| 能力 | 说明 |
|------|------|
| 🌍 多城联程 | 任意复杂路线 + 混合交通 + 智能距离推断 |
| 🔄 自愈丰富 | 模糊输入自动补充具体推荐，绝不放弃 |
| 🍽️ 零泛化推荐 | 每个餐厅/景点/住宿都是具体真实地名 |
| 📸 拍照机位 | 每天 2-3 个具体位置 + 最佳时间 + 拍摄建议 |
| 💰 5 类预算 | 大交通/住宿/当地交通/门票/餐饮，含明细 |
| 🎨 5 种风格 | 轻松版/省钱版/亲子版/美食版/拍照版一键切换 |
| 👥 同伴感知 | solo/couple/family/friends/group/business |
| 🏨 住宿品牌推荐 | 按档位推荐真实酒店品牌 |
| ✏️ 交互精修 | 自然语言调整 + 逐日确认/重规划 |
| 🌦️ 天气感知 | 按季节推荐穿搭和活动 |
| 🔀 行程对比 | 两个行程并列对比 |
| 📋 打包清单 | AI 根据行程自动生成 |
| 📝 旅行日记 | 按日生成日记模板 |
| 🎲 随机推荐 | 不知道去哪时推荐目的地 |
| 📕 偏好提取 | 从攻略/笔记中提取旅行偏好 |
| 🗣️ 中英双语 | 默认中文，English auto-switch |

---

## 🔧 架构 / Architecture

```
用户输入（自由文本）
    │
    ▼
Stage 1 — 语义提取
    ├── 提取全部维度（12+ 项）
    ├── 质量自检 → 不足则自动丰富 + 重试
    └── 输出结构化 Schema
    │
    ▼
Stage 2 — 行程生成
    ├── 同伴适配 + 节奏控制 + 住宿推荐 + 预算策略
    ├── 逐日生成（活动/三餐/拍照/住宿/可行性）
    └── 城市导览 + 贴士 + 预算明细
    │
    ▼
交互精修
    ├── 自然语言调整
    ├── 风格变体切换
    └── 逐日确认/重规划
```

---

## 👤 作者 / Author

**BrightyLudwig** — [github.com/BrightyLudwig](https://github.com/BrightyLudwig)

---

## 📄 许可 / License

MIT
