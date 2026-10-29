[English](README.md) | [简体中文](README.zh-CN.md) | [Español](README.es.md) | [Português (Brasil)](README.pt-BR.md) | [日本語](README.ja.md)

# 🎃 Trick-or-Treat TriPeaks — 月光桥万圣节三峰纸牌

**三座牌塔，一路糖果，再留一座月光桥。** Trick-or-Treat TriPeaks 是为 [FreeCell Game](https://freecell-game.top/) 创作的万圣节三峰纸牌游戏。连接相邻点数，清空牌峰，利用连续收牌赚来的月光桥接续断开的路线。黑猫 J、女巫 Q 和南瓜 K 都是专门绘制的原创牌面。

**[在线试玩](https://halloween-tripeaks.crazy3d.org/)** · [万圣节游戏总合集](https://github.com/AshinTop/halloween-games) · [嵌入说明](EMBEDDING.md) · [设计说明](DESIGN.md)

**文档语言：** English、简体中文、Español、Português (Brasil)、日本語。**游戏界面目前仅支持英语和简体中文**；西班牙语、葡萄牙语和日语版本为完整说明文档，并非已实现的界面翻译。

![万圣节 TriPeaks 三峰纸牌，展示三座牌峰、牌库、弃牌和月光桥进度](docs/images/gameplay.jpg)

## 牌桌上有什么？👻

- 一副完整的 **52 张牌**：牌峰 28 张、牌库 23 张，另有 1 张起始弃牌。
- **8 局旅程关卡**，每局都有无需抽牌即可完成的已验证路线。
- 可复现的经典洗牌与按 UTC 日期生成的每日挑战。
- 有限的月光桥、撤销、合法一步提示、星级、本地存档和可关闭的合成音效。

## 怎样清空三座牌峰

选择一张未被压住、点数比当前弃牌大一或小一的牌，将它移到弃牌堆顶。花色和颜色不影响连接，A 与 K 可以首尾相连，所以 **K–A–2** 是合法路线。压在一张牌上的牌必须全部移走，它才会露出。清空全部 28 张牌峰牌即获胜。

可以随时从牌库抽下一张，抽牌会重置连击。23 张牌库牌只能使用一遍，不能回收重发。只有同时满足「牌库已空、没有可接的明牌、没有月光桥」才判定失败。

连续正常收走五张牌可以获得**月光桥**。同时最多持有一座，每局最多获得两座。先选月光桥，再选任意未被压住的牌，就能忽略点数限制收走它。被压住的牌依然不能选。使用月光桥会重置连击，再点一次按钮可取消选择。撤销会恢复纸牌、牌库、分数和魔法资源。

普通收牌得 10 分加当前连击数 × 5；移走峰顶牌额外得 50 分。月光桥收牌获得基础 10 分及可能的峰顶奖励。获胜时，未抽牌得三星，抽牌不超过五次得两星，其余胜局得一星。没有倒计时。

## 操作

| 操作 | 方法 |
|---|---|
| 收走纸牌 | 点击或轻触；也可 Tab 聚焦后 Enter |
| 从牌库抽牌 | 点击牌库；焦点不在按钮或输入框时按空格 |
| 使用魔法 | 先点月光桥，再点明牌 |
| 撤销 | Z 或撤销按钮 |
| 高亮合法一步 | 找一步提示 |
| 重玩或更换模式 | 重开与模式选择 |

**「找一步」只提示当前合法动作，不是完整求解器。** 现在能收走的牌，不代表后面一定能赢。

## 选择与分享牌局

[旅程 1](https://halloween-tripeaks.crazy3d.org/?level=1) 是固定关卡的起点。[经典种子 12345](https://halloween-tripeaks.crazy3d.org/?mode=classic&seed=12345) 可分享同一副洗牌；再次选择经典模式会生成新局，重开则保留当前牌局。[指定日期的每日挑战](https://halloween-tripeaks.crazy3d.org/?mode=daily&date=2026-10-31) 固定使用对应的 UTC 日期。

当前进度、最佳成绩和偏好保存在本地。链接参数明确指定牌局时，会打开该局。撤销历史仅在本次页面会话中保留。

## 常见问题

**每一局都能解开吗？** 八局旅程关卡有测试验证的完整解。经典随机牌局和每日牌局不保证有解。

**月光桥能拿走被压住的牌吗？** 不能。它只放宽点数限制，不改变遮挡规则。

**牌库用完能再翻一遍吗？** 不能。何时抽牌、如何延长连击、何时用桥，正是这款游戏的策略所在。

## 图文与视频

![紧凑 TriPeaks 窗口，牌角点数、弃牌与月光桥控件清晰排列](docs/images/mobile.jpg)

截图来自真实浏览器中的紧凑 iframe，用于说明布局，不代表实体手机性能测试。

[观看 24 秒介绍视频](https://halloween-tripeaks.crazy3d.org/intro.html) · [下载带字幕 MP4](docs/media/intro.mp4)。视频无声，由实际游戏截图编排而成，并非连续操作录像。截图和视频记录的是拍摄时的界面，可能早于后续视觉细节更新。

## 嵌入你的站点

```html
<iframe src="https://halloween-tripeaks.crazy3d.org/"
  title="Trick-or-Treat TriPeaks"
  style="display:block;width:100%;height:654px;border:0"
  allow="fullscreen" allowfullscreen></iframe>
```

纸牌会随实际窗口调整，适配桌面、窄竖屏和短横屏布局。请给 iframe 设置真实高度，让牌角点数有足够空间。游戏不访问父页面，也不需要麦克风、摄像头或指针锁定。

在线版本通过 GitHub 关联部署到 Cloudflare。请为 iframe 设置实际高度，并给主站工具栏留出空间；全屏入口可由主站提供。详细约定见 [EMBEDDING.md](EMBEDDING.md)。

## 本地运行与规则验证

```sh
python3 -m http.server 4173
```

在仓库根目录启动静态服务，再打开 [http://localhost:4173/](http://localhost:4173/)。游戏无需构建或安装依赖。请使用 HTTP(S)，直接双击 `file://` 页面可能阻止 ES 模块加载。运行测试需要 Node.js。

```sh
npm test
```

**12 项测试**覆盖八局旅程的完整解、整副牌唯一性、遮挡关系、A/K 连接、牌库行为、月光桥获取与上限、准确的失败条件、可复现洗牌、日期链接和存档校验。

游戏源码不依赖账号、远程 API、广告 SDK 或外部素材 CDN。记录保存在当前浏览器，不提供云端同步；Cloudflare 可能另外加入托管脚本与请求日志。可选合成音效遵循浏览器的声音权限。

## 下一段月光小冒险 🍬

- [Haunted FreeCell](https://halloween-freecell.crazy3d.org/) · [源码](https://github.com/AshinTop/halloween-freecell) — 经典空当接龙与灯笼救援残局.
- [Pumpkin Shift](https://halloween-pumpkin-shift.crazy3d.org/) · [源码](https://github.com/AshinTop/halloween-pumpkin-shift) — 带月光滑行的数字滑块谜题.
- [Witch’s Candy Blocks](https://halloween-block-blast.crazy3d.org/) · [源码](https://github.com/AshinTop/halloween-block-blast) — 8×8 糖果方块摆放消除.
- [Pumpkin 2048](https://halloween-2048.crazy3d.org/) · [源码](https://github.com/AshinTop/halloween-2048) — 经典合并与灯笼试炼.

## 制作说明与支持

为 **AshinTop 的 Midnight Candy Club** 创作，设计、编程、文案、测试与审查由人类指导的 AI 协作完成。原创插画和浏览器合成声音为本项目制作，创作意图可见 [设计说明](DESIGN.md)。

喜欢这段小冒险？欢迎 **[给 Trick-or-Treat TriPeaks 点一颗 GitHub Star](https://github.com/AshinTop/halloween-tripeaks)**，方便收藏并关注更新。反馈问题时，请附关卡或模式、浏览器、窗口大小和复现步骤。还可以逛逛 [完整万圣节合集](https://github.com/AshinTop/halloween-games)。
