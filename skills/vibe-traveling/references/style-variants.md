# Style Variants & Companion Injection

## Companion Injection

Translate companion type into concrete activity, dining, and hotel choices:

| Companion | Activity Bias | Dining Bias | Hotel Bias |
|-----------|--------------|-------------|------------|
| **solo** | Solo-friendly routes, museums, walking tours | Single-diner restaurants, counter seats, food courts | Hostels, capsule hotels, budget chains |
| **couple** | Romantic viewpoints, sunset spots, couple photo ops | Window seats, candlelight settings, shared plates | Boutique hotels, rooms with views, bathtubs |
| **friends** | Group activities, nightlife, adventure sports | Social dining, BBQ, big tables, craft beer | Central locations, multi-bed rooms, lively areas |
| **family** | Kid-friendly attractions, playgrounds, zoos | Family restaurants with kids' menus, casual dining | Family rooms, safe neighborhoods, kitchenettes |
| **group** | Easy logistics, book-ahead attractions, moderate pace | Private rooms, set menus, big round tables | Chain hotels with group rates, meeting facilities |
| **business** | Near meeting venues, efficient routing, reliable transport | Quiet settings for conversation, power outlets | Business hotels near CBD, meeting rooms |

## Pace Control

| Pace | Spots/Day | Start Time | Meal Breaks | Transport |
|------|-----------|------------|-------------|-----------|
| **relaxed** | 2-3 | Late morning OK | 1.5-2 hours | Taxi/private car preferred |
| **moderate** | 3-4 | 9 AM typical | 1-1.5 hours | Mix of metro + taxi |
| **intensive** | 4-6 | 8 AM sharp | Quick bites | Metro + walking, efficient routing |

## Hotel Brand Recommendations by Tier

| Tier | Chinese Brands | International Brands | Price/Night |
|------|---------------|---------------------|-------------|
| **budget** | 如家 / 汉庭 / 7天 / 海友 | ibis / Super 8 | ≤200 CNY |
| **comfort** | 全季 / 亚朵 / 桔子 / 维也纳 | Holiday Inn Express / Mercure | 200-500 CNY |
| **luxury** | 万达文华 / 首旅建国 | Marriott / Hilton / InterContinental / Hyatt | 600+ CNY |
| **boutique** | 花间堂 / 松赞 / 既下山 | Aman / Banyan Tree / Six Senses | varies |

## Style Variants

When the user triggers a variant, regenerate the entire itinerary with these overrides:

### 轻松版 (Relaxed)
**Triggers:** "轻松" "休闲" "慢慢来" "放松" "不想太赶"
**Behavior:**
- Max 2-3 spots per day
- Late morning starts (10am OK)
- 2h lunch breaks, generous free time
- More hotel/rest downtime
- Prefer taxi over metro for comfort

### 省钱版 (Budget)
**Triggers:** "省钱" "穷游" "便宜" "经济" "预算有限"
**Behavior:**
- Public transit only (bus/metro)
- Budget hotels (≤200 CNY/night)
- Free or low-cost attractions prioritized
- Street food and food courts over restaurants
- Lower all budget estimates by 30-40%

### 亲子版 (Family)
**Triggers:** "亲子" "带娃" "小孩" "宝宝" "孩子"
**Behavior:**
- Kid-friendly attractions (zoos, science museums, amusement parks)
- Maximum 2-3 spots/day regardless of stated pace
- Playground/rest breaks built in every afternoon
- Family restaurants with kids' menus
- Hotels with family rooms or connecting rooms

### 美食版 (Foodie)
**Triggers:** "美食" "吃货" "吃" "吃的" "美食之旅"
**Behavior:**
- Route organized around restaurants and food streets
- Night markets and food districts prioritized
- Cut low-food-value scenic spots to make room
- 4 meals/day (breakfast/lunch/dinner/supper or snack stop)
- Each meal: detailed dish recommendations + local specialties

### 拍照版 (Photo)
**Triggers:** "拍照" "出片" "打卡" "摄影" "拍照好看"
**Behavior:**
- Scenic spots prioritized over content-deep attractions
- Sunrise/sunset timing for key locations
- Instagram-worthy hotels and cafes
- 3+ photo spots per day with detailed timing
- Golden hour windows noted explicitly
