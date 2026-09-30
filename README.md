# 印花趋势中心

静态单页站点：TOP 商品 · 市场趋势 · 节日活动 · 传品类目 · 运营联系

## 目录结构

```
├── index.html          # 主页面（约 1MB）
├── images/
│   ├── top/            # 趋势商品图 + 二维码（WebP，约 5MB）
│   └── qr/             # 原始联系人二维码备份
└── README.md
```

## 部署到 GitHub Pages（推荐）

1. 在 GitHub 新建空仓库（例如 `print-trend-center`）
2. 本地执行：

```bash
cd github-deploy
git init
git add .
git commit -m "印花趋势中心：图片外置 WebP 版"
git branch -M main
git remote add origin https://github.com/你的用户名/仓库名.git
git push -u origin main
```

3. 仓库 **Settings → Pages**
   - Source：Deploy from a branch
   - Branch：`main` / `/ (root)`
   - 保存后等待 1–2 分钟
4. 访问：`https://你的用户名.github.io/仓库名/`

## 体积说明

| 项目 | 原版 | 本版 |
|------|------|------|
| 单文件 HTML | ~63 MB（base64 内嵌） | ~0.9 MB |
| 图片 | 内嵌 | 独立 WebP ~5 MB |
| 总计 | 63 MB 一次下载 | 首屏小，图片按需加载 |

所有 `<img>` 已加 `loading="lazy"` + `decoding="async"`。

## 本地预览

```bash
# 任意静态服务器
npx serve .
# 或
python3 -m http.server 8080
```

浏览器打开 `http://localhost:8080` 即可。

## 注意

- 不要再把图片 base64 写回 HTML
- 新增商品图请放到 `images/top/`，在 HTML 里用相对路径引用
