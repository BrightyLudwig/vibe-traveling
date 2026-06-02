---
name: vibe-traveling
description: AI travel planner that turns free-text Chinese travel ideas into complete day-by-day itineraries. Use when the user wants to plan a trip, generate travel routes, get destination recommendations, or create detailed travel schedules.
author: BrightyLudwig
key: SHA256:yE2rGMDGWK3ScxZdO79m2LKyxEENy9YfW2hTqyBGa1k
---

# Vibe Traveling ✈️

From one sentence to a complete travel plan. Tell me your travel vibe — where, how long, with whom, what you love — and I'll craft a full executable itinerary.

## When to Use

- User says "帮我规划一次旅行" / "我想去XX玩" / "推荐一个目的地"
- User describes a travel idea and wants a concrete plan
- User wants budget estimates, route optimization, or itinerary refinement
- User asks about destinations, weather, food, or travel logistics

## How to Plan

### Step 1 — Understand the Vibe

Extract from the user's input (ask clarifying questions if vague):

| Dimension | What to Extract |
|-----------|----------------|
| Origin | Departure city |
| Destinations | All cities/stops, including side trips |
| Dates / Duration | Total days, start date |
| Companion | Solo / couple / friends / family / group |
| Pace | Relaxed (2-3 spots/day) / Moderate (3-4) / Intensive (4-6) |
| Budget level | Budget / Comfort / Luxury |
| Hotel preference | Area, style, star level |
| Food vibe | Local cuisine / fine dining / street food / specific cuisines |
| Interests | Nature / history / city life / shopping / adventure / photo |
| Transport | Self-driving / high-speed rail / flight / mixed |
| Special needs | Accessibility / pet-friendly / halal / vegetarian / kid-friendly |

### Step 2 — Build the Schema

Structure the trip into a clear schema:

```
Origin → [Segment 1: City A, N days, transport] → [Segment 2: City B, M days] → Return
```

For each inter-city move, infer the best transport mode:
- ≤ 100 km → self-driving
- 100–600 km → high-speed rail
- > 600 km → flight

### Step 3 — Generate the Full Itinerary

For EACH day, produce:

**Day Card:**
- Day number, date, day type (stay / transit / return)
- A catchy title with specific place names
- Weather-aware activity suggestions

**Activities (3-5 categories per day):**
- 上午 / 下午 / 晚上 / 交通 / 住宿
- Every item MUST name a real, specific place — NEVER use generic fillers like "当地景点" or "某餐厅"
- For transit days: specific transport info with estimated duration and cost

**Meals (2-3 per day):**
```json
{
  "type": "breakfast|lunch|dinner|snack",
  "name": "Real restaurant name",
  "cuisine": "Cuisine type",
  "pricePerPerson": 80,
  "address": "Approximate location",
  "mustTry": "Signature dish"
}
```

**Photo Spots (2-3 per day):**
- Specific shooting location + best time of day
- Example: "断桥残雪 — 清晨 6:30-7:30 光线最佳，从北山路口进入"

**Hotel (per city):**
- Real hotel name or specific area recommendation
- Price range, style, reason for recommendation

**Feasibility Check:**
- Score (1-100), status (easy / balanced / heavy)
- Why this day works, what risks to note

### Step 4 — Add the Extras

**City Guide Cards** (for each unique city):
- City name (Chinese + English)
- Emoji that captures its vibe
- 4-6 specific highlights
- One vivid sentence

**Travel Tips:**
- Packing suggestions (weather-aware)
- Transport tips
- Food recommendations
- Safety / cultural notes
- Budget-saving tricks (if applicable)

**Budget (5 categories, in CNY):**

| Category | What to Include |
|----------|----------------|
| 大交通 | Every inter-city segment as separate line items |
| 住宿 | Hotel nights × nightly rate per city |
| 当地交通 | Metro / taxi / bus / rental car |
| 门票 | Every attraction with real ticket prices |
| 餐饮 | Meals × days based on budget level |

**Budget guidelines by level:**
- Budget: 100-150/day/person for meals, budget hotels ≤200/night
- Comfort: 200-350/day/person for meals, mid-range hotels 200-500/night
- Luxury: 400-600/day/person for meals, high-end hotels 600+/night

## Style Variants

If the user asks for a specific vibe, apply these overrides:

- **轻松版 (Relaxed)**: Max 2-3 spots/day, late starts OK, generous breaks, more hotel downtime
- **省钱版 (Budget)**: Public transit, budget hotels, free attractions, street food, lower cost estimates
- **亲子版 (Family)**: Kid-friendly attractions, slower pace, playground breaks, family restaurants
- **美食版 (Foodie)**: Restaurant-focused routing, food streets, local specialties, fewer low-value stops
- **拍照版 (Photo)**: Scenic spots prioritized, sunrise/sunset timing, Instagram-worthy hotels and routes

## Output Format

Present the itinerary in clear, well-structured Chinese. Use:

1. **Overview card**: Route summary, dates, total budget
2. **Day-by-day timeline**: Each day with activities, meals, photo spots
3. **City guides**: One card per city
4. **Budget table**: 5 categories with line items
5. **Travel tips**: Categorized suggestions
6. **Map summary**: Describe the route geographically

## Quality Standards

- Every place name MUST be real and specific
- Every restaurant MUST have a name, cuisine type, and approximate price
- Budget must be internally consistent (category sum ≈ total)
- Days must chain correctly (yesterday's arrival = today's starting point)
- Transport modes must match distances
- If the user's input is vague, ENRICH it — suggest specific destinations, attractions, and restaurants
- Never recommend non-existent routes or impossible logistics

## Example

**User input:** "从南京自驾去杭州玩3天，然后高铁去深圳，飞机回南京，一周左右，舒服一点，喜欢本地菜"

**Response should include:**
- Route: 南京 → 杭州 (3天, 自驾) → 深圳 (2天, 高铁) → 南京 (返程, 飞机)
- Day 1: 杭州西湖 + 楼外楼午餐 + 龙井村下午茶 + 银泰晚餐
- Day 2: 灵隐寺 + 法喜寺 + 满觉陇 + 杭帮菜博物馆
- ... (every day with real names)
- Budget: ~¥5,200/人 (detailed 5-category breakdown)
- Map description: 南京出发经沪宁高速至杭州，高铁沿海线至深圳，飞机返程
