# QQMCBridge+ 官网（静态站）

QQMCBridge+（原插件 QQMCBridge 的魔改增强版）官方网页。

## 相关仓库

| 仓库 | 说明 | 地址 |
| --- | --- | --- |
| QQMCBridgeplus-LSE | 增强版 · BDS 端 LLSE 插件主体（JavaScript） | https://github.com/fengyushaonian/QQMCBridgeplus-LSE |
| QQMCBridgeplus_python-adaptar | 增强版 · Python 网关（图卡渲染 / pymods / Web 面板） | https://github.com/fengyushaonian/QQMCBridgeplus_python-adaptar |
| QQMCBridge | 原版 / 上游项目，作者 JERC-STUDIO | https://github.com/JERC-STUDIO/QQMCBridge |

首页「开源仓库」区块、下载区按钮、页脚与 404 页均已指向以上地址，改动链接时四处同步。

## 目录结构

```
website/
├── index.html            # 官网首页
├── 404.html              # GitHub Pages 404 页
├── favicon.ico
├── QQMCBridge-release.zip   # 插件发布包（下载按钮指向）
├── .nojekyll             # 让 GitHub Pages 跳过 Jekyll 处理
├── assets/
│   ├── main.css          # 基础样式（复用 Mass 模板）
│   ├── site.css          # 扩展区块样式
│   ├── mc-theme.css      # Minecraft 风格主题（方块贴图已 base64 内嵌）
│   ├── main.js           # 交互脚本（chip 旋转 / 网格高亮 / 导航）
│   ├── remixicon.woff2   # 图标字体
│   └── fonts/
│       └── Minecraft-Tenv2.woff2   # Minecraft 像素字体
└── res/                  # 方块贴图源素材（16x16，已内嵌进 mc-theme.css）
    ├── grass-block.png
    ├── dirt.png
    ├── stone.webp
    └── diamond_block.webp
```

## 部署到 GitHub Pages

两种方式任选：

### 方式 A：仓库根目录（推荐）
把 `website/` 里的**全部文件**（含隐藏的 `.nojekyll`）推到仓库根目录，然后在
`Settings → Pages → Build and deployment → Source` 选择 `Deploy from a branch`，
分支选 `main`，目录选 `/ (root)`。保存后等待 1~2 分钟即可访问：

```
https://<你的用户名>.github.io/<仓库名>/
```

### 方式 B：docs/ 目录
把 `website/` 内容放到仓库的 `docs/` 目录，Pages 来源选 `Deploy from a branch`，
分支 `main`、目录选 `/docs`。

## 本地预览

```bash
cd website
python -m http.server 8501
# 浏览器打开 http://127.0.0.1:8501/
```

## 注意事项

- **不要改动 res/ 里的贴图后忘记同步**：四张贴图已 base64 内嵌在 `assets/mc-theme.css`，
  直接改 `res/` 文件不会生效；如需换图，请同步更新 CSS 里的 `data:image/...`。
- 所有资源引用均为**相对路径**，部署在任意子路径下都能正常工作（GitHub Pages
  对无尾斜杠的访问会自动 301 重定向到带 `/` 的 URL）。
- 更换新发布包时，直接覆盖 `QQMCBridge-release.zip` 即可。
