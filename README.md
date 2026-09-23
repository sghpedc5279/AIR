# 《档案智能管理》智能书

**在线地址**：<https://sghpedc5279.github.io/AIR/>

苏州大学社会学院 · 图情档方向课程教材，含 **9 个部分**，其中第九部分为「人工智能前沿与档案智能管理」专章。

## 站点结构

| 文件 / 目录 | 说明 |
|---|---|
| `index.html` | 首页，提供「在线阅读」与「章节下载」两个入口 |
| `book.html` | 互动翻页教材（**由 CI 从 `src/` 自动生成**，勿手工编辑） |
| `download.html` | 章节 Word 文档下载页 |
| `chapters/` | 10 篇按部分拆分的 docx（图片已内嵌，静态下载资源） |
| `src/` | **可编辑源**：`NN_标题.md` 按部分拆分，直接改这里即可改教材 |
| `build_flipbook.py` `build_html.py` `quotes_bank.py` `split_md_source.py` | 翻页生成与源拆分脚本（零第三方依赖） |
| `.github/workflows/deploy-pages.yml` | GitHub Actions：推送即由 `src/` 重建 `book.html` 并部署 |

## 阅读操作

- 键盘 `←` `→` 翻页 · `T` 打开目录 · `F` 全屏
- 点击任意图片可全屏查看（灯箱），`Esc` 关闭

## 如何修改教材（推荐：直接改 `src/`）

`book.html` 不再手工维护，改 `src/` 里的源文件即可：

1. 在 GitHub 上直接编辑 `src/XX_部分标题.md`，或本地改完提交；
2. 推送到 `main` 分支，GitHub Actions 会自动：
   - 运行 `python build_flipbook.py --src src --book ar` 重建 `book.html`；
   - 部署到 Pages。

本地预览生成结果：

```bash
cd air-pages
python build_flipbook.py --src src --book ar   # 生成 book.html
```

## 如果你仍习惯编辑整本 Markdown

教材正文主稿仍是 `档案智能管理_智能书编写.md`（位于工作区）。改完后用
`split_md_source.py` 重新生成 `src/` 即可，后续流程不变：

```bash
cd "C:\Users\sghpe\Desktop\BaiduSyncdisk\两本教材"
python split_md_source.py --book ar
# 再把 air-pages/src/ 提交推送
```

## 课堂互动

教材已按部分拆分为 10 篇 docx，可**批量导入飞书知识库**（导入为在线文档 → Microsoft Word），
学生即可在文档中使用「划词评论」参与课堂讨论与提问。

## 部署方式

GitHub Actions 自动部署，推送到 `main` 分支即触发。

> 仓库 **Settings → Pages → Build and deployment → Source** 已设为 **GitHub Actions**。
