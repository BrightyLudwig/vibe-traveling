# Examples

## Example 1 — Multi-city, Chinese

**Input:**
> 从南京自驾去杭州玩3天，然后坐高铁去深圳，最后飞机回南京，总共一周左右，住舒适型酒店，喜欢吃本地菜

**Stage 1 — Extracted Schema:**
- origin: 南京
- segments:
  - {from:南京, to:杭州, days:3, transport:自驾, note:西湖/灵隐寺/龙井村}
  - {from:杭州, to:深圳, days:2, transport:高铁, note:世界之窗/欢乐海岸/华侨城}
- finalReturn: {from:深圳, to:南京, transport:飞机}
- companion: friends (default)
- pace: moderate
- budgetLevel: medium
- hotelLevel: comfort
- cuisine: 本地特色
- totalDays: 7
- vibes: [foodie, culture, nature]

**Stage 2 — Output Highlights:**
- Day 1 (stay, 杭州): 西湖游船 → 楼外楼(lunch, ¥120/人, 西湖醋鱼) → 苏堤步行 → 雷峰塔 → 湖滨晚餐
- Day 2 (stay, 杭州): 灵隐寺 → 法喜寺 → 满觉陇 → 杭帮菜博物馆
- Day 3 (stay, 杭州): 龙井村茶园 → 九溪烟树 → 之江校区
- Day 4 (transit, 杭州→深圳): 高铁G85, ~7h, ¥600 → 深圳湾公园夜景
- Day 5 (stay, 深圳): 世界之窗 → 欢乐海岸lunch → 华侨城创意园
- Day 6 (return, 深圳→南京): 飞机CZ3825, ~2.5h, ¥900
- Budget: ~¥5,200/人 (~$720 USD)

---

## Example 2 — English, Solo

**Input:**
> Tokyo to Kyoto for 4 days, then Osaka 2 days, back to Tokyo. Mid-budget, love ramen and photography, traveling solo.

**Stage 1 — Extracted Schema:**
- origin: Tokyo
- segments:
  - {from:Tokyo, to:Kyoto, days:4, transport:train, note:Fushimi Inari/Kinkakuji/Arashiyama}
  - {from:Kyoto, to:Osaka, days:2, transport:local train, note:Dotonbori/Osaka Castle}
- finalReturn: {from:Osaka, to:Tokyo, transport:train}
- companion: solo
- pace: moderate
- budgetLevel: medium
- interests: photo

**Stage 2 — Output Highlights:**
- Day 1 (transit+stay, Kyoto): Shinkansen Tokyo→Kyoto → Fushimi Inari (7am for empty torii shots) → Nishiki Market lunch → Kiyomizudera at sunset
- Day 2 (stay, Kyoto): Arashiyama Bamboo Grove (6:30am, before crowds) → Tenryuji → Kinkakuji → Pontocho dinner
- Day 3 (stay, Kyoto): Philosopher's Path → Nanzenji → Gion at dusk
- Day 4 (stay→transit, Kyoto→Osaka): Fushimi Inari revisit → local train to Osaka → Dotonbori at night (neon reflections)
- Day 5 (stay, Osaka): Osaka Castle → Shinsekai → Kuromon Market → Umeda Sky Building sunset
- Day 6 (return, Osaka→Tokyo): Shinkansen return, ~2.5h
- Budget: ~¥85,000/person (~$590 USD) excluding international flights
- Photo spots: torii tunnel (7am), bamboo grove (6:30am), Dotonbori neon (8pm), golden pavilion reflection (10am)

---

## Example 3 — Style Variant Switch

**Input:**
> (After receiving a plan) "换成拍照版"

**Behavior:**
1. Record current plan as undo snapshot
2. Apply Photo variant overrides: scenic priority, sunrise/sunset timing, Instagram-worthy venues
3. Regenerate entire trip with photo-first routing
4. Notify user they can undo with "撤销" or "退回之前的版本"

---

## Example 4 — Natural Language Refinement

**Input:**
> "第三天太赶了，放慢一点，再加个博物馆"

**Behavior:**
1. Identify Day 3 in current itinerary
2. Read Day 2 and Day 4 context (neighbor-day awareness)
3. Reduce activities from 5→3, shift non-essential items to other days
4. Add a museum appropriate to the city and user's interests
5. Replace only Day 3, keep all other days intact
6. Recalculate affected budget items

---

## Example 5 — Vague Input Enrichment

**Input:**
> "想去云南玩几天"

**Stage 1 — Auto-Enrich:**
- Input is too vague (no cities, no duration, no preferences)
- Enrich Round 1: suggest classic Yunnan route
  - origin: (ask or infer from IP location, default 北京)
  - segments: 昆明(2d,飞机) → 大理(2d,高铁) → 丽江(2d,高铁)
  - totalDays: 6
  - note: 石林/滇池, 苍山/洱海, 丽江古城/玉龙雪山
  - companion: friends, pace: moderate, budgetLevel: medium
- Present enriched schema to user for confirmation before Stage 2
