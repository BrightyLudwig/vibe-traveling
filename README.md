# ✈️ Vibe Traveling — Claude Code Skill

> **Tell me your travel vibe, I'll craft the journey.**
>
> A Claude Code skill that turns free-text travel ideas into complete, executable day-by-day itineraries — with real place names, detailed budgets, photo spots, and style variants.

---

## What It Does

This skill teaches Claude to be your personal AI travel planner. Describe your trip in natural language — multi-city, multi-transport, any preferences — and get back a structured, actionable itinerary.

### One Sentence → Full Plan

```
你说：从南京自驾去杭州玩3天，高铁去深圳，飞机回南京，一周，喜欢本地菜

Claude 输出：
✅ 完整路线图（城市链 + 交通方式）
✅ 逐日详细行程（景点 + 餐厅 + 住宿 + 拍照机位）
✅ 5 类预算明细（大交通/住宿/当地交通/门票/餐饮）
✅ 城市导览卡片（含特色亮点）
✅ 旅行贴士（打包/交通/美食/安全）
✅ 可行性评估（每天节奏评分）
```

---

## Install

```bash
claude plugins install BrightyLudwig/vibe-traveling
```

Or manually:

```bash
git clone https://github.com/BrightyLudwig/vibe-traveling.git ~/.claude/skills/vibe-traveling
```

## Usage

In Claude Code, type `/vibe-traveling` and describe your trip idea.

Or just talk naturally — Claude will invoke the skill when you say things like:
- "帮我规划一次去云南的旅行"
- "推荐一个适合情侣的周末目的地"
- "我想去成都和重庆玩5天，怎么安排"

---

## Features

| Feature | Description |
|---------|-------------|
| 🌍 **Multi-city routing** | Any complex route with mixed transport |
| 🚗 **Smart transport** | Auto-infers drive/train/flight by distance |
| 🍽️ **Real recommendations** | Specific restaurants, not "当地美食" |
| 📸 **Photo spots** | Best shooting locations + optimal timing |
| 💰 **5-category budget** | Transport / Hotel / Local transit / Tickets / Meals |
| 🎨 **5 style variants** | Relaxed / Budget / Family / Foodie / Photo |
| 👥 **Companion-aware** | Solo / couple / friends / family / group |
| 🌦️ **Weather-aware** | Season-appropriate activity suggestions |
| 🛡️ **Quality checks** | Distance logic, budget consistency, route continuity |

---

## Why "Vibe" Traveling?

Traditional travel planning is about logistics — booking tickets, finding hotels, checking boxes. **Vibe traveling** is about capturing the *feeling* you want from a trip and translating it into a concrete plan.

You describe the vibe; Claude handles the details.

---

## License

MIT
