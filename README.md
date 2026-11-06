# 赤途云迹 · 红色文旅一站式平台

以红色文化旅游为主题的多页站点：把主题路线、红色故事、景点购票和运营后台放在同一套页面里，全部由静态 HTML / CSS / JavaScript 实现，无需构建工具。

---

## 项目概览

- **形态**：纯前端多页应用（MPA），双击 `src/index.html` 即可浏览，没有 npm 依赖、没有构建步骤。
- **页面**：15 个，覆盖首页聚合、6 个红色故事详情、4 个高德地图路线演示、登录 / 注册 / 购票 / 后台演示。
- **数据**：全部硬编码在前端（JS 数组或页面内联），不依赖后端接口。
- **交互**：路线卡片、新旧照片对比滑块、轮播图、地图路线与节点打卡、后台图表与表格管理，均为可演示的前端原型。

## 页面地图

| 页面                                                     | 说明                                                                          |
| :------------------------------------------------------- | :---------------------------------------------------------------------------- |
| [`src/index.html`](src/index.html)                       | 首页：精选旅游路线、红色景点购票（轮播 + 购票入口）、红色景点推荐、红色故事区 |
| [`src/jingGangShan.html`](src/jingGangShan.html)         | 井冈山革命根据地 · 红色故事                                                   |
| [`src/nanchangUprising.html`](src/nanchangUprising.html) | 南昌起义 · 红色故事                                                           |
| [`src/Yudu.html`](src/Yudu.html)                         | 红军长征出发地（于都）· 红色故事                                              |
| [`src/ludingBridge.html`](src/ludingBridge.html)         | 飞夺泸定桥 · 红色故事                                                         |
| [`src/zunyiConference.html`](src/zunyiConference.html)   | 遵义会议 · 红色故事                                                           |
| [`src/yanAn.html`](src/yanAn.html)                       | 延安 · 红色故事                                                               |
| [`src/jingGangShanDemo.html`](src/jingGangShanDemo.html) | 井冈山路线地图演示                                                            |
| [`src/yanAnDemo.html`](src/yanAnDemo.html)               | 延安路线地图演示                                                              |
| [`src/zuiYiDemo.html`](src/zuiYiDemo.html)               | 遵义路线地图演示                                                              |
| [`src/xiBanPoDemo.html`](src/xiBanPoDemo.html)           | 西柏坡路线地图演示                                                            |
| [`src/purchaseTickets.html`](src/purchaseTickets.html)   | 红色景点预约购票                                                              |
| [`src/adminConsole.html`](src/adminConsole.html)         | 运营后台：数据图表、地点管理、打卡管理、基础配置                              |
| [`src/login.html`](src/login.html)                       | 登录（前端模拟）                                                              |
| [`src/register.html`](src/register.html)                 | 注册（前端模拟 + 表单校验）                                                   |

地图演示页统一提供：鼠标样式切换、地图级别与中心点、可拖拽标记点、显示范围限制、比例尺 / 工具条 / 方向盘 / 鹰眼、路线连线与节点红旗打卡。

## 目录结构

```text
Match
├── docs/
│   ├── projectDocumentation.md      # 项目文档（立项 / 答辩 / 验收）
│   └── developmentDocumentation.md  # 开发文档（实现与维护细节）
├── src/
│   ├── index.html                   # 首页
│   ├── *.html                       # 故事页 / 地图演示页 / 购票 / 后台 / 登录注册
│   ├── components/
│   │   └── Javascript/              # 各页面复用的脚本
│   └── static/
│       ├── css/                     # 各页面样式
│       └── image/                   # 图片资源（新旧对比照、轮播图等）
├── .gitignore
└── README.md
```

## 前端模块

**JavaScript**（`src/components/Javascript/`）

| 文件               | 作用                                         | 使用页面            |
| :----------------- | :------------------------------------------- | :------------------ |
| `routeList.js`     | 首页路线卡片：数据 + 模板拼接 + 点击委托     | `index.html`        |
| `splicing.js`      | 红色故事区：六组新旧照片对比卡片             | `index.html`        |
| `cloudCarousel.js` | 首页购票轮播的左右切换（首尾循环）           | `index.html`        |
| `mapReuse.js`      | 地图演示通用逻辑，暴露 `initMapDemo(config)` | 4 个 `*Demo.html`   |
| `maps.js`          | 高德地图 JSAPI 2.0 本地副本（压缩版）        | 4 个 `*Demo.html`   |
| `chart.js`         | Chart.js v4.6.1 本地副本                     | `adminConsole.html` |

**CSS**（`src/static/css/`）

| 文件                   | 作用                                                        |
| :--------------------- | :---------------------------------------------------------- |
| `index.css`            | 首页整体布局与板块样式                                      |
| `gongluechakan.css`    | 红色景点推荐列表（`.spot-item` / `.spot-name` / `.rating`） |
| `lunbotu.css`          | 轮播图与导航点、左右箭头                                    |
| `lunbotutiaozhuan.css` | 购票跳转按钮                                                |
| `mapDemo.css`          | 地图演示页面板与标记样式                                    |
| `adminConsole.css`     | 后台页面样式                                                |
| `search.css`           | 通用面板 / 按钮样式（当前未被引用）                         |
| `mapComponent.css`     | 地图面板、红旗、打卡弹窗样式（当前未被引用）                |

## 运行方式

```bash
# 方式一：直接打开
# 双击 src/index.html（file:// 协议即可运行，页面间为相对路径）

# 方式二：本地静态服务器（推荐，便于调试与相对路径解析）
# 访问 http://127.0.0.1:8000/src/index.html
```

注意事项：

- 地图演示页需要联网加载高德瓦片；`maps.js` 只是 JSAPI 本地副本，底图仍需网络。
- 页面之间通过 `./xxx.html`、`./static/...` 相对路径互相引用，**请勿拆散 `src/` 目录结构**。
- `register.html` 通过 CDN 引入 Font Awesome 图标，离线打开时图标会缺失，其余样式不影响。

## 数据与配置入口

| 位置                                | 内容                                                  |
| :---------------------------------- | :---------------------------------------------------- |
| `routeList.js` → `ROUTE_DATA`       | 首页 4 条主题路线（名称、简介、标签、行程节点、天数） |
| `splicing.js` → `redStories`        | 红色故事区 6 组卡片（新旧照片、时间、标题）           |
| `*Demo.html` → `initMapDemo({...})` | 每条地图路线的名称、中心点、缩放、显示范围、节点坐标  |
| `adminConsole.html`                 | 后台的地点、打卡、配置等演示数据（页面内联）          |
| `purchaseTickets.html`              | 购票页景点与预约表单（页面内联）                      |

要新增一条地图路线，复制任意 `*Demo.html`，只改 `initMapDemo({...})` 里的 6 个配置即可，无需复制地图逻辑。

## 已知限制

- 没有后端：登录、注册、购票、后台增删改均为前端演示，刷新后不保留数据。
- 故事详情页各自内联 `<style>`，样式存在重复，后续可抽成公共样式表。
- 以下文件当前未被任何页面引用：`mapComponent.js`、`mapComponent.css`、`textScrolling.js`、`search.css`，可按需清理。

## 项目文档

- [项目文档](docs/projectDocumentation.md)：项目背景、需求分析、页面规划、实施与验收说明。
- [开发文档](docs/developmentDocumentation.md)：目录约定、模块职责、样式规范与维护细节。

## 开发约定

**分支**：`main` 保持可交付；功能从 `main` 切出 `feat/<name>`，修复使用 `fix/<name>`。

**提交**：遵循 [Conventional Commits](https://www.conventionalcommits.org/)，格式 `type(scope): subject`。

| type       | 用途                   |
| :--------- | :--------------------- |
| `feat`     | 新增页面或功能         |
| `fix`      | 修复缺陷               |
| `style`    | 不影响逻辑的样式调整   |
| `refactor` | 重构，不改变外部行为   |
| `docs`     | 文档变更               |
| `chore`    | 构建、配置、资源等杂项 |
