# Budget Specification

## 5 Fixed Categories

Always produce exactly these 5 categories. Never add "其他" or extra categories.

| # | Name (CN) | Name (EN) | What to Include |
|---|-----------|-----------|----------------|
| 1 | 大交通 | Intercity Transport | Every intercity segment as separate line items. N segments = N items. |
| 2 | 住宿 | Accommodation | Number of overnight stays × nightly rate. Transit/return days: no hotel cost. |
| 3 | 当地交通 | Local Transit | Metro/taxi/bus/rental car per day. Estimate based on city size. |
| 4 | 门票 | Tickets & Activities | Each attraction with real ticket prices. Mark free ones explicitly. |
| 5 | 餐饮 | Meals | (Total days - transit days) × daily meal budget per budget tier. |

## Budget Tiers (CNY)

| Tier | Meals/Day/Person | Hotel/Night | Local Transport/Day | Strategy |
|------|-----------------|-------------|---------------------|----------|
| **low** | 100-150 | ≤200 | 20-40 | Public transit first → free attractions → control dining |
| **medium** | 200-350 | 200-500 | 40-80 | Comfort baseline |
| **high** | 400-600 | 600+ | 80-200 | Private car/VIP → fine dining → premium experiences |

## Output Structure

```
budget:
  perPerson: <total per person in CNY>
  total: <grand total in CNY>
  categories:
    - name: "大交通"
      total: <sum>
      items:
        - name: "南京→杭州 高铁二等座"
          cost: 150
          range: "120-200"
    - name: "住宿"
      total: <sum>
      items: [...]
    - name: "当地交通"
      total: <sum>
      items: [...]
    - name: "门票"
      total: <sum>
      items: [...]
    - name: "餐饮"
      total: <sum>
      items: [...]
  assumptions:
    - "按2人出行估算"
    - "酒店价格按淡季参考"
  confidence: high|medium|low
```

## Validation Rules

- Category sums must approximately equal the declared total (≤30% deviation)
- Transport category must have ≥1 item per intercity segment
- Hotel per-night cost must fall within the stated tier range
- Meal budget must be realistic for the destination city
