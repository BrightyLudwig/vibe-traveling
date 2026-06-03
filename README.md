# ✈️ Vibe Traveling

> **一句话 → 完整旅行方案 | One sentence → Complete travel plan**
>
> 默认中文，English supported. Claude Code · ChatGPT · Gemini · DeepSeek · 任意 LLM Agent.

[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](./LICENSE)
[![Claude Code](https://img.shields.io/badge/Claude%20Code-Skill-0891b2)](./skills/vibe-traveling/SKILL.md)
[![Author](https://img.shields.io/badge/Author-BrightyLudwig-orange)](https://github.com/BrightyLudwig)

---

## 📦 安装 / Install

### Claude Code
```bash
claude plugins install BrightyLudwig/vibe-traveling
```

### ChatGPT / Gemini / DeepSeek / Cursor / 其他 Agent
复制 [`PROMPT.md`](./PROMPT.md) → 粘贴到 System Prompt / Instructions 中即可。

---

## 🧠 能力

- **两阶段流程**：语义提取 → 质量自检 → 自动丰富 → 行程生成
- **零泛化**：每个推荐都是具体真实地名，不用"当地景点""某餐厅"
- **5 种风格**：轻松版 / 省钱版 / 亲子版 / 美食版 / 拍照版
- **5 类预算**：大交通 / 住宿 / 当地交通 / 门票 / 餐饮，含明细项
- **交互精修**：自然语言调整、逐日确认/重规划、风格切换、行程对比
- **扩展**：拍照机位、打包清单、旅行日记、随机目的地、偏好提取
- **中英双语**：默认中文，English auto-switch

## 📂 文件

```
vibe-traveling/
├── .claude-plugin/plugin.json         # Claude Code 插件元数据
├── skills/vibe-traveling/
│   ├── SKILL.md                        # Skill 入口（紧凑，<200行）
│   └── references/
│       ├── style-variants.md           # 风格变体 + 同伴适配详细说明
│       ├── budget-spec.md              # 预算规范 + 档位参考
│       └── examples.md                 # 完整输入→输出示例
├── PROMPT.md                           # 通用系统提示词（任意 Agent 可用）
└── README.md
```

## 📄 License

MIT
