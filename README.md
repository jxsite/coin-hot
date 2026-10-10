# CoinHOT — 加密货币 AI 精选日报站

🌐 **在线访问：https://jxsite.github.io/coin-hot/**

模仿 [aihot.news](https://aihot.news) 的产品形态（AI 聚合 → 两轮评分 → 中文摘要 → 每日日报），把行业从 AI 换成**加密货币**的每日精选新闻站。

## 每天更新什么

- 首页「今日精选」：当天最重要的加密新闻，每条带 **AI 评分**、中文标题、摘要与一句话推荐理由，均链接原文
- 「往期日报」：按日归档
- `feed.xml`：RSS 订阅

## AI 流水线（每天自动运行）

1. **采集**：8 家加密媒体 RSS（CoinDesk / CoinTelegraph / The Block / Decrypt / CryptoSlate / BeInCrypto / Bitcoin.com News / U.Today），按权威度分 T1 / T1_5 / T2 三级，抓取后去重
2. **预筛**：只留加密行业相关，剔除广告、标题党价格预测、无信息增量的通稿
3. **AI 两轮评分**（0–100，五维加权：重要性 35% / 时效性 15% / 信息增量 20% / 信源权威 15% / 读者价值 15%），两次取平均；T1 ≥ 60、T1_5 ≥ 65、T2 ≥ 76 入选
4. **写作归组**：中文标题 + 答案先行的摘要 + 推荐理由；同一事件多家报道归组为一条
5. **发布**：生成静态站并推送到 GitHub Pages

详细算法说明见站内「算法说明」页。

## 本地构建

```bash
cd collector && python3 collect.py 30 raw.jsonl   # 采集
# 精选与撰写（AI 步骤）-> curated/<date>.json
python3 render.py                                  # 生成 site/
```

仅供信息参考，不构成投资建议。
