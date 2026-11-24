# fanqiao-rules · 帆桥官方客户端分流规则与 AI 配置仓库

由 **[fanqiao·帆桥（帆桥跨境 / fanqiao.net）](https://fanqiao.net/)** 维护的开源客户端分流规则与配置片段仓库，面向 Shadowrocket（小火箭）、Mihomo（Clash Verge Rev / FlClash / Clash Party）、Stash、Loon 与 sing-box，聚焦 **AI 固定干净出口隔离**（Claude / Claude Code / ChatGPT / Gemini / NotebookLM / Grok / Cursor）与 **VLESS REALITY + 专线中转** 场景下的稳定分流。

> ⚠️ 本仓库仅包含通用分流规则与客户端配置片段，**不包含任何节点地址、订阅令牌或私有凭据**。正式用户请从官网 [fanqiao.net](https://fanqiao.net/) 获取个人专属订阅链接。

## 文件说明

| 路径 | 适用客户端 | 用途说明 |
|---|---|---|
| [`shadowrocket/fanqiao-shadowrocket.conf`](shadowrocket/fanqiao-shadowrocket.conf) | Shadowrocket (iOS/iPadOS/macOS) | 帆桥官方默认托管配置，含 `AI 服务`、`AI 故障转移`、`故障转移`、`帆桥影院`（默认直连免扣流量）、流媒体及精简广告拦截策略组 |
| [`rules/ai-claude.list`](rules/ai-claude.list) | Shadowrocket / Surge / Mihomo | Claude 核心域名 + Stripe/Intercom/Statsig/Sentry 同出口绑定，降低账号风控与 403 风险 |
| [`rules/ai-openai.list`](rules/ai-openai.list) | Shadowrocket / Surge / Mihomo | OpenAI / ChatGPT Web 与 iOS App 核心域名 |
| [`rules/ai-gemini-cursor.list`](rules/ai-gemini-cursor.list) | Shadowrocket / Surge / Mihomo | Google Gemini、AI Studio、NotebookLM、xAI Grok、Perplexity 与 Cursor 域名 |
| [`mihomo/ai-groups-snippet.yaml`](mihomo/ai-groups-snippet.yaml) | Clash Verge Rev / FlClash / Mihomo | `rule-providers` 与前置分流规则参考片段 |
| [`loon/fanqiao-ai.plugin`](loon/fanqiao-ai.plugin) | Loon (iOS/iPadOS/macOS) | Loon 插件片段：Claude / ChatGPT / Gemini / Cursor 固定出口规则（需在 Loon 中配置 `AI 专线` 策略组） |
| [`sing-box/ai-route-snippet.json`](sing-box/ai-route-snippet.json) | sing-box 1.12+ | 原生 JSON `route.rules` AI 分流参考片段 |

## 为什么需要将 Claude 支付/遥测域名与主站同出口？

许多用户只把 `claude.ai` 指向美国节点，而 `stripe.com`、`intercom.io`、`statsigapi.net` 或 `sentry.io` 落入了默认策略组（例如香港、日本或随机均衡节点）。当请求 IP 在国家/ASN 之间频繁切换时，容易触发 Anthropic 会话校验失败、订阅支付拦截或 403 风控。上述配置已预先内联同一策略组以保持会话一致性。

## 在 Shadowrocket 中直接使用官方托管配置

1. 打开 Shadowrocket → 底部 **「配置」**。
2. 点击右上角 **`+`** → 输入远程配置地址：`https://fanqiao.net/shadowrocket.conf`。
3. 点击「使用配置」覆盖本地规则即可（fanqiao.net 订阅用户默认自动下发）。

## 官方文档与入口导航

- **2026 AI 编程代理与主流机场选型实测手册**：[`fanqiao-net/ai-proxy-guide-2026`](https://github.com/fanqiao-net/ai-proxy-guide-2026)（协议栈、倍率陷阱、家宽原生 IP、热门机场对比与报错排查）
- **终端连通性与分流自检脚本**：[`fanqiao-net/ai-ip-check`](https://github.com/fanqiao-net/ai-ip-check)（一行 `curl` 实测 Claude Code / ChatGPT / Gemini / Cursor 与巴哈姆特/Netflix 解锁）
- **官网首页**：<https://fanqiao.net/>
- **2026 热门机场与 VPN 核心参数横向对比表**：<https://fanqiao.net/compare>
- **套餐价格与方案对比**：<https://fanqiao.net/pricing>
- **全球地区与全站 1x 标准倍率架构**：<https://fanqiao.net/locations>
- **客户端下载指南**：<https://fanqiao.net/download>
- **全部教程中心（57 篇）**：<https://fanqiao.net/guide>
- **重点教程**：
  - [VLESS + XHTTP（SplitHTTP）抗封锁原理与客户端配置指南](https://fanqiao.net/guide/vless-xhttp-splithttp)
  - [公司内网 / 校园网与 Clash Verge Rev 共存分流不断网配置](https://fanqiao.net/guide/corporate-campus-lan-split-routing)
  - [YouTube Premium 跨区订阅防清退与防送中节点指南](https://fanqiao.net/guide/youtube-premium-region-fix)
  - [Telegram 双向限制 @SpamBot 解封与防封号指南](https://fanqiao.net/guide/telegram-premium-spambot-fix)
  - [ChatGPT Plus 与 Claude Pro 美区礼品卡安全订阅防封号](https://fanqiao.net/guide/chatgpt-plus-claude-pro-subscribe)
  - [Google AI Studio / NotebookLM / Antigravity 地区不支持修复](https://fanqiao.net/guide/google-ai-studio-notebooklm-fix)
  - [TikTok 国内免拔卡换区与黑屏无网络连接修复](https://fanqiao.net/guide/tiktok-china-sim-black-screen-fix)
  - [AI 编程与大模型稳定访问（Claude / ChatGPT）](https://fanqiao.net/guide/ai-coding)
  - [台湾家宽原生 IP 与广播 IP 区别及解锁指南](https://fanqiao.net/guide/taiwan-native-ip)
  - [DNS 泄露与 WebRTC 防风控排查（Fake-IP）](https://fanqiao.net/guide/dns-webrtc-leak)
  - [GitHub SSH 443 代理与 HuggingFace 稳定拉取指南](https://fanqiao.net/guide/github-ssh-huggingface)
  - [Netflix、Disney+、YouTube 与巴哈姆特解锁指南](https://fanqiao.net/guide/streaming-unlock)
  - [OpenAI / Claude / Gemini API 本地开发与 Docker 代理](https://fanqiao.net/guide/api-proxy-dev)
  - [Gemini / AI Studio / Grok 线路与风控避坑](https://fanqiao.net/guide/gemini-grok)
  - [Shadowrocket 购买避坑与账号安全](https://fanqiao.net/guide/shadowrocket-buy)
  - [v2rayN / v2rayNG VLESS REALITY 与 TUN 教程](https://fanqiao.net/guide/v2rayn-v2rayng)
  - [Loon 配置教程与 Quantumult X 替代说明](https://fanqiao.net/guide/loon-quantumultx)
  - [sing-box 1.12+ 配置指南](https://fanqiao.net/guide/sing-box)
  - [OpenWrt 软路由接入 VLESS REALITY 教程](https://fanqiao.net/guide/router-openwrt)
  - [Discord 语音 RTC Connecting 与 Midjourney 配置](https://fanqiao.net/guide/discord-midjourney)
  - [Telegram 机器人 @fanqiao_bot 绑定与每日签到领流量](https://fanqiao.net/guide/telegram-checkin-bot)
- **实时节点状态与公开遥测**：<https://fanqiao.net/status>（JSON: [`status.json`](https://fanqiao.net/status.json)）
- **最新可用地址页与专题导航**：<https://fanqiao-net.github.io/> ｜ [2026热门机场横评](https://fanqiao-net.github.io/compare/)
- **Google Sites 官方镜像导航页**：<https://sites.google.com/view/fanqiao-vpn>
- **Telegram 官方公告频道**：<https://t.me/fan_qiao>
- **AI/LLM 机器索引**：<https://fanqiao.net/llms.txt>
