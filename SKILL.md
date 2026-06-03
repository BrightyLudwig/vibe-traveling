---
name: vibe-traveling
description: AI travel planner — turn free-text travel ideas into complete day-by-day itineraries. Supports Chinese & English. 一句话生成完整旅行方案，默认中文。Use when users want to plan a trip, generate travel routes, or get destination recommendations.
author: BrightyLudwig
---

# Vibe Traveling ✈️

> **默认语言：中文 | English supported — reply in user's language**

---

## 一、这是什么 / What It Does

**中文（默认）**：从一句话到完整旅行方案。告诉 Claude 你的旅行想法——去哪儿、几天、和谁、喜欢什么——Claude 会生成一份可直接执行的逐日行程，包含真实地名、餐厅推荐、拍照机位、预算明细。

**English**: From one sentence to a complete travel plan. Tell Claude your travel vibe — where, how long, with whom, what you love — and get back a full executable day-by-day itinerary with real place names, restaurant picks, photo spots, and budget breakdowns.

---

## 二、使用方式 / When to Use

### 中文触发（默认）
- "帮我规划一次旅行"
- "我想去XX玩几天"
- "推荐一个适合XX的目的地"
- "帮我优化一下这个行程"

### English Triggers
- "Plan a trip to..."
- "I want to visit..."
- "Recommend a destination for..."
- "Help me build an itinerary for..."

---

## 三、规划流程 / How It Works

### Step 1 — 理解旅行意图 / Understand the Vibe

从用户输入中提取以下维度（模糊时主动追问）：

| 维度 / Dimension | 提取内容 / What to Extract |
|------------------|---------------------------|
| 出发地 / Origin | Departure city |
| 目的地 / Destinations | All cities/stops, including side trips |
| 时间 / Duration | Total days, start date |
| 同伴 / Companion | Solo / couple / friends / family / group |
| 节奏 / Pace | 轻松(2-3个点/天) / 适中(3-4) / 紧凑(4-6) |
| 预算 / Budget | 省钱 / 舒适 / 高端 |
| 住宿偏好 / Hotel | Area, style, star level |
| 美食偏好 / Food | Local cuisine / fine dining / street food / specific cuisines |
| 兴趣 / Interests | Nature / history / city / shopping / adventure / photo |
| 交通 / Transport | 自驾 / 高铁 / 飞机 / 混合 |
| 特殊需求 / Special | 无障碍 / 亲子 / 宠物 / 清真 / 素食 |

### Step 2 — 构建路线 / Build the Schema

```
Origin → [Segment 1: City A, N days, transport] → [Segment 2: City B, M days] → Return
```

**智能交通推断 / Smart Transport Inference：**
- ≤ 100 km → 自驾 / self-driving
- 100–600 km → 高铁 / high-speed rail
- > 600 km → 飞机 / flight

### Step 3 — 生成逐日行程 / Generate Day-by-Day

每天产出 / Each Day Includes：

```
📅 Day N — 日期 | 类型(stay/transit/return) | 标题（含具体地名）

🌅 上午 / Morning  → 2-3 个具体活动（必须真实地名）
🌤️ 下午 / Afternoon→ 2-3 个具体活动
🌙 晚上 / Evening  → 1-2 个具体活动

🍽️ 三餐 / Meals (2-3 per day):
   { type, name(真实餐厅名), cuisine, pricePerPerson, address, mustTry }

📸 拍照机位 / Photo Spots (2-3 per day):
   "具体位置 — 最佳拍摄时间 + 拍摄建议"

🏨 住宿 / Hotel:
   { name, area, priceRange, style, reason }

⚖️ 可行性 / Feasibility:
   { score(1-100), status(easy|balanced|heavy), reasons, warnings }
```

### Step 4 — 扩展内容 / Add Extras

- **城市卡片 / City Guides**：每城一张，含 emoji + 英文名 + 4-6 亮点 + 一句话
- **旅行贴士 / Travel Tips**：打包、交通、美食、安全、省钱技巧
- **预算表 / Budget**：5 类固定结构

---

## 四、预算规范 / Budget Spec

| 类别 Category | 内容 What to Include |
|---------------|---------------------|
| 大交通 / Transport | 每一段城际交通独立列出 |
| 住宿 / Accommodation | 每晚 × 天数 |
| 当地交通 / Local Transit | 地铁/打车/公交/租车 |
| 门票 / Tickets | 每个景点真实票价 |
| 餐饮 / Meals | 正餐 × 天数，按预算档位 |

**预算档位 / Budget Tiers：**

| 档位 | 餐饮 / 天 / 人 | 住宿 / 晚 | 使用 CNY |
|------|---------------|-----------|----------|
| 省钱 Budget | 100-150 | ≤200 | ✅ |
| 舒适 Comfort | 200-350 | 200-500 | ✅ |
| 高端 Luxury | 400-600 | 600+ | ✅ |

> **注意**：预算用 CNY，括号标注等值 USD/EUR（约 ¥1 = $0.14 = €0.13）。

---

## 五、风格变体 / Style Variants

| 变体 | 中文说明 | English |
|------|---------|---------|
| 轻松版 | 每天 2-3 个点，晚起，充裕休息 | Relaxed: max 2-3 spots/day, late starts OK |
| 省钱版 | 公共交通、经济酒店、免费景点、街头小吃 | Budget: public transit, budget hotels, free attractions |
| 亲子版 | 亲子友好景点、慢节奏、儿童餐厅 | Family: kid-friendly, slow pace, family restaurants |
| 美食版 | 餐厅驱动路线、美食街、本地特色 | Foodie: restaurant-first routing, street food focus |
| 拍照版 | 景点优先、日出日落时间、高颜值路线 | Photo: scenic priority, golden hour timing |

---

## 六、质量标准 / Quality Standards

- ✅ **每个地名必须真实具体** — 禁止"当地景点""某餐厅"等泛化表述
- ✅ **每个餐厅必须有名有价** — 含菜系、人均、地址、必点菜
- ✅ **预算内部一致** — 类别合计 ≈ 总预算
- ✅ **路线连贯** — 前一天到达 = 后一天出发
- ✅ **交通匹配距离** — 不推荐不合理路线
- ✅ **模糊则丰富** — 用户输入含糊时主动补充具体推荐
- ✅ **回复语言** — 默认中文，用户用英文则英文回复

---

## 七、示例 / Example

**中文输入：**
> "从南京自驾去杭州玩3天，然后高铁去深圳，最后飞机回南京，一周左右，舒服一点，喜欢本地菜"

**输出应包含：**
- 路线：南京 → 杭州(3天,自驾) → 深圳(2天,高铁) → 南京(返程,飞机)
- Day 1: 西湖 + 楼外楼午餐 + 龙井村下午茶 + 湖滨银泰晚餐
- Day 2: 灵隐寺 + 法喜寺 + 满觉陇 + 杭帮菜博物馆
- ... 每天具体地名
- 预算：~¥5,200/人（5 类明细）
- 地图：沪宁高速→杭州，高铁沿海线→深圳，飞机返程

**English input:**
> "Tokyo to Kyoto for 4 days, then Osaka 2 days, back to Tokyo, mid-budget, love ramen and photography"

**Output should include:**
- Route: Tokyo → Kyoto (4d, Shinkansen) → Osaka (2d, local train) → Tokyo (return, Shinkansen)
- Day 1: Fushimi Inari (7am for empty shots) + Nishiki Market lunch + Kiyomizudera sunset
- ... real names every day
- Budget: ~¥85,000/person (~$590 USD)
