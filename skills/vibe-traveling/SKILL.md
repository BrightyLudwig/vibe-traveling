---
name: vibe-traveling
description: Generates complete day-by-day travel itineraries from free-text Chinese or English trip descriptions. Use when the user wants to plan a trip, generate travel routes, get destination recommendations, refine an itinerary, switch travel styles, or compare travel plans.
---

# ✈️ Vibe Traveling

Turn a travel idea into a complete, executable day-by-day itinerary. Every recommendation must be a real, specific place name — zero generic filler.

## When to Use

- "帮我规划一次旅行" / "Plan a trip to..."
- User describes a trip idea and wants a detailed plan
- User wants to refine, restyle, or replan an existing itinerary
- User asks for budget estimates, packing lists, or travel tips
- User pastes travel notes (Xiaohongshu / blog) to extract preferences

## When NOT to Use

- User only wants flight/hotel search (use OTA search tools)
- User asks for real-time pricing or booking (you provide estimates, not live data)
- User asks for visa/immigration legal advice

## Two-Stage Workflow

### Stage 1 — Extract & Enrich

Extract ALL of these dimensions from the user's input. **If any dimension is vague or empty, enrich it proactively — never return a fuzzy result.**

| Dimension | Extraction Rule |
|-----------|----------------|
| origin | Real city name. Never use placeholder text. |
| segments[] | Each: from / to / days / transport / note (specific attractions) |
| startDate | Default to tomorrow. Format YYYY-MM-DD. |
| finalReturn | REQUIRED. Default: round-trip to origin. Never hallucinate. |
| companion | solo / couple / friends / family / group / business |
| pace | relaxed / moderate / intensive |
| budgetLevel | low / medium / high |
| hotelLevel | budget / comfort / luxury / boutique |
| hotelArea | Preferred neighborhood — infer if not stated |
| cuisine | Food preferences — infer from context |
| interests | Museums / nature / nightlife / shopping / adventure / photo |
| special | Accessibility / halal / vegetarian / pet-friendly |
| styleVariant | Relaxed / Budget / Family / Foodie / Photo (see `references/style-variants.md`) |
| vibes[] | Up to 4 from: adventure / foodie / culture / relaxation / nature / urban / romantic / family / photo / budget / luxury / wellness |

**Self-healing quality gate:**
- If segment notes average < 5 characters → input is too vague → auto-enrich and retry
- Retry up to 2 rounds. Never give up.
- "XX周边" → propose 1-2 specific nearby destinations as separate segments
- "当天返回XX" → split into independent return segment (do NOT merge)

**Transport inference by distance:**
- ≤ 100 km → self-driving
- 100–600 km → high-speed rail
- > 600 km → flight

### Stage 2 — Generate

Generate the complete itinerary. **Every preference parameter must become a concrete behavioral instruction**, not a passive label.

**Companion injection** — see `references/style-variants.md#companion-injection` for full details.
**Style variant injection** — see `references/style-variants.md#style-variants` for full details.

**Each day MUST include:**

| Element | Requirement |
|---------|------------|
| day / date / type | Day number from 1, date from startDate, type = stay\|transit\|return |
| location | Specific city/district/route |
| title | Catchy title with real place names |
| 上午 / 下午 / 晚上 | 2-3 concrete activities per slot. **Zero generics.** |
| transport | mode / label / duration / costRange |
| meals[] | Each: type / name / cuisine / pricePerPerson / address / mustTry |
| photoSpots[] | 2-3 per day, each with location + best time + shooting tip |
| hotel | name / area / priceRange / style / reason |
| hotelAdvice | area / why / budget / convenience |
| feasibility | score(1-100) / status(easy\|balanced\|heavy) / reasons[] / warnings[] |

**Banned words — NEVER use:**
"当地景点" "某餐厅" "某酒店" "随便吃" "附近转转" "自行探索"

### Iterative Refinement

After the initial plan is generated, respond to natural-language adjustments:
- "第三天太赶了" → replan Day 3 with neighbor-day context
- "换成美食版" → apply Foodie variant, regenerate entire trip
- "Day 2 确认" → mark Day 2 confirmed, track progress
- "对比这两个方案" → produce side-by-side comparison

## Budget

Always produce exactly 5 categories. See `references/budget-spec.md` for tier tables and format details.

| # | Category | Contents |
|---|----------|----------|
| 1 | 大交通 | Every intercity segment as a separate line item |
| 2 | 住宿 | Overnight stays × nightly rate |
| 3 | 当地交通 | Metro / taxi / bus, estimated per day |
| 4 | 门票 | Real ticket prices for each attraction |
| 5 | 餐饮 | Non-transit days × daily meal budget |

Amounts in CNY. Add USD/EUR equivalents in parentheses.

## Output Format

1. **Route overview** — city chain, transport modes, dates
2. **Day-by-day timeline** — full detail per day
3. **City guides** — one card per city (name/en/emoji/gradient/highlights/desc)
4. **Travel tips** — 4-5 categories with icon + items
5. **Budget table** — 5 categories with line items
6. **Feasibility** — per-day score and warnings

Default language: Chinese. Reply in English if the user writes in English.

## Examples

See `references/examples.md` for detailed input→output pairs.

### Quick Example

**Input:** "从南京自驾去杭州玩3天，高铁去深圳，飞机回南京，一周，舒服一点，喜欢本地菜"

**Output must include:**
- Route: 南京 → 杭州(3d,自驾) → 深圳(2d,高铁) → 南京(return,飞机)
- Day 1: 西湖 + 楼外楼(lunch, 杭帮菜, ¥120/人, 孤山路30号, 必点西湖醋鱼) + 龙井村 + ...
- Budget: ~¥5,200/人 (5 categories with line items)
- City cards for 杭州 and 深圳
- Feasibility scores and warnings for each day
