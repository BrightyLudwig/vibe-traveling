# ✈️ Vibe Traveling — Claude Code Skill

> **一句话 → 完整旅行方案 | One sentence → Complete travel plan**
>
> 默认中文，English supported. 让 Claude 成为你的 AI 旅行管家。

[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](./LICENSE)
[![Claude Code Skill](https://img.shields.io/badge/Claude%20Code-Skill-0891b2)](./SKILL.md)
[![Author](https://img.shields.io/badge/Author-BrightyLudwig-orange)](https://github.com/BrightyLudwig)

---

## 📖 这是什么 / What

**Vibe Traveling** 是一个 Claude Code Skill，让 Claude 变身为 AI 旅行规划师。你描述旅行想法，Claude 生成完整可执行的逐日行程。

- 🗣️ **自然语言输入**：说"人话"就行，不用填表单
- 📋 **端到端输出**：路线 + 行程 + 餐厅 + 住宿 + 拍照 + 预算，一次性全给
- 🌏 **中英双语**：默认中文，自动适配用户语言
- 🎨 **5 种风格**：轻松版 / 省钱版 / 亲子版 / 美食版 / 拍照版

---

## 🚀 安装 / Install

```bash
# Claude Code 一键安装
claude plugins install BrightyLudwig/vibe-traveling
```

或手动安装 / Or manually:

```bash
git clone https://github.com/BrightyLudwig/vibe-traveling.git \
  ~/.claude/skills/vibe-traveling
```

---

## 💡 使用 / Usage

在 Claude Code 中输入 `/vibe-traveling`，然后描述你的旅行想法。

或直接自然对话 — Claude 会自动触发 skill：

| 中文 | English |
|------|---------|
| "帮我规划一次去云南的旅行" | "Plan a trip to Kyoto for me" |
| "推荐一个周末情侣目的地" | "Recommend a weekend getaway" |
| "我想去成都重庆玩5天" | "Help me plan 5 days in Thailand" |
| "这个行程太赶了，放松一点" | "Make the itinerary more relaxed" |

---

## 🧠 能力 / Capabilities

<table>
<tr><th>能力</th><th>Capability</th><th>说明</th></tr>
<tr><td>🌍 多城联程</td><td>Multi-city routing</td><td>任意复杂路线 + 混合交通</td></tr>
<tr><td>🚗 智能交通</td><td>Smart transport</td><td>按距离自动推断自驾/高铁/飞机</td></tr>
<tr><td>🍽️ 真实推荐</td><td>Real recommendations</td><td>具体餐厅名+菜系+人均+必点，绝不泛化</td></tr>
<tr><td>📸 拍照机位</td><td>Photo spots</td><td>每天 2-3 个最佳拍摄位置+时间</td></tr>
<tr><td>💰 5 类预算</td><td>5-category budget</td><td>大交通/住宿/当地交通/门票/餐饮</td></tr>
<tr><td>🎨 5 种风格</td><td>5 style variants</td><td>轻松/省钱/亲子/美食/拍照</td></tr>
<tr><td>👥 同伴感知</td><td>Companion-aware</td><td>独行/情侣/朋友/家庭/商务</td></tr>
<tr><td>🌦️ 季节感知</td><td>Season-aware</td><td>根据季节推荐合适活动和穿搭</td></tr>
<tr><td>🛡️ 质量校验</td><td>Quality checks</td><td>距离逻辑+预算一致性+路线连贯</td></tr>
<tr><td>🗣️ 中英双语</td><td>Bilingual</td><td>默认中文，English auto-switch</td></tr>
</table>

---

## 📋 输入示例 / Input Examples

### 中文
```
从南京自驾去杭州玩3天，然后坐高铁去深圳，最后飞机回南京，
总共一周左右，住舒适型酒店，喜欢吃本地菜
```

### English
```
Flying from London to Rome for 4 days, train to Florence for 2 days,
fly back. Love art and pasta, mid-range budget, traveling solo.
```

### 一句话调整 / One-sentence Refinement
```
"第三天太赶了，放慢节奏"  →  Claude 重新规划 Day 3
"把酒店换到西湖边上"      →  Claude 更新住宿推荐
"变成美食版"              →  Claude 切换为美食风格
```

---

## 🏗️ Skill 结构 / Structure

```
vibe-traveling/
├── SKILL.md      ← Claude Code skill 定义（核心）
└── README.md     ← 项目说明
```

没有外部依赖，不包含任何第三方代码。Skill 是纯 Prompt 工程——通过精心设计的指令让 Claude 成为旅行规划师。

---

## 👤 作者 / Author

**BrightyLudwig**

- GitHub: [github.com/BrightyLudwig](https://github.com/BrightyLudwig)
- Key: `SHA256:yE2rGMDGWK3ScxZdO79m2LKyxEENy9YfW2hTqyBGa1k`

---

## 📄 许可 / License

MIT
