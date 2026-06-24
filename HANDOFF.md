# 日本旅游项目 · 交接给 Claude

> 最后更新：2026-06-24 | 项目负责人：Eve | 工具：trip-map-builder skill

---

## 项目文件

```
C:\Users\86198\Documents\trip-japan-july\
├── index.html      ← 地图页面（已部署）
├── index-v1.html   ← V1 备份
├── plan-v1.md      ← V1 行程存档
└── plan-v2.md      ← 当前行程
```

- **GitHub**: https://github.com/Eveyqr/trip-japan-july
- **在线地图**: https://eveyqr.github.io/trip-japan-july/
- **工具 skill**: `trip-map-builder`（~/.hermes/skills/trip-map-builder/）

---

## 当前行程 V2 · 关东+关西 6日

| 天 | 日期 | 行程 | 住 |
|---|---|---|---|
| D1 | 7/10 周四 | 东京着陆 → 东京塔 → Shibuya Sky 🌃 | 新宿 |
| D2 | 7/11 周五 | 浅草寺/晴空塔 → 镰仓高校前 → 新干线→大阪 | 难波 |
| D3 | 7/12 周六 | USJ 全天 🔒 | 难波 |
| D4 | 7/13 周日 | 黑门市场 → 下午去京都 → 伏见稻荷 | 京都 |
| D5 | 7/14 周一 | 清水寺 → 二三年坂 → 祇园 → 锦市场 | 京都 |
| D6 | 7/15 周二 | Haruka 特急 → 关西机场 → 广州 ✈️ | — |

- 人数：5-6人团
- 预算：人均 ≈¥7,000（含机票酒店吃饭门票）
- D2 关键：退房行李寄存前台，镰仓回来取，不用拖箱子跑

---

## Phase 进度

| Phase | 状态 | 说明 |
|-------|------|------|
| 1 行程规划 | ✅ 完成 | plan-v2.md |
| 2 餐厅调研 | ❌ 未开始 | V2 换了行程，V1 的餐厅数据不适用 |
| 3 地图生成 | ✅ 完成 | HTML 已部署，但餐厅数据是临时填的 |

---

## Phase 2 待做 · 餐厅调研

用 `trip-map-builder` skill 的 Phase 2 流程：

1. **搜小红书**：`opencli xiaohongshu search` 搜各地餐厅
2. **提取信息**：店名、人均、必点菜、排队情况
3. **写回 HTML**：把 `DAYS` 数组里的 `food` location 补充 detail、pay、xhsKeyword

需搜的城市/区域：
- 东京 D1：东京塔/涩谷附近晚餐
- 镰仓 D2：小町通午饭
- 大阪 D4：黑门市场具体摊位推荐
- 京都 D4 晚餐 + D5 午饭/锦市场

**注意**：大众点评不支持日本城市，只用小红书搜。skill 里有完整的小红书搜索流程（references/xhs-research.md）。

---

## Phase 3 地图页面说明

`index.html` 是单文件 Leaflet 地图，结构：
- `DAYS[]` 数组：每天的 location 数据
- `overviewContent()` 函数：总览页
- 支持：点击导航（Apple/Google/高德）、点击打开小红书搜索、预约按钮
- 部署到 GitHub Pages，手机直接打开即看

---

## 关键约束

1. **不删文件、不擅自外发**
2. 改 HTML 前先备份
3. 餐厅信息要有小红书笔记做依据，不编造
4. 坐标注意关东（139.x）vs 关西（135.x），不要串

---

## Eve 的偏好

- 语气轻松直接，不要废话
- 做完汇报结果即可，不用总结
- 有问题直接问，不乱猜
- 出发前别忘了：🍣 Omakase 预约、🎢 USJ Express Pass、💴 换日元
