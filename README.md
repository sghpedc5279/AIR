# 《档案智能管理》智能书

**在线地址**：<https://sghpedc5279.github.io/AIR/>

苏州大学社会学院 · 图情档方向课程教材，含 **9 个部分**，其中第九部分为「人工智能前沿与档案智能管理」专章。

## 站点结构

| 文件 | 说明 |
|---|---|
| `index.html` | 首页，提供「在线阅读」与「章节下载」两个入口 |
| `book.html` | 互动翻页教材，146 页，16:9 显示，单文件离线可用 |
| `download.html` | 章节 Word 文档下载页 |
| `chapters/` | 10 篇按部分拆分的 docx（图片已内嵌） |
| `.github/workflows/deploy-pages.yml` | GitHub Actions 自动部署配置 |

## 阅读操作

- 键盘 `←` `→` 翻页 · `T` 打开目录 · `F` 全屏
- 点击任意图片可全屏查看（灯箱），`Esc` 关闭

## 课堂互动

教材已按部分拆分为 10 篇 docx，可**批量导入飞书知识库**（导入为在线文档 → Microsoft Word），
学生即可在文档中使用「划词评论」参与课堂讨论与提问。

## 更新内容

教材正文维护在 `档案智能管理_智能书编写.md`。改完后：

```bash
cd "C:\Users\sghpe\Desktop\BaiduSyncdisk\两本教材"

# 1. 重新生成翻页教材（用普通 Python 即可；build_flipbook.py 会同时重算两本）
python build_flipbook.py
cp "档案智能管理_互动翻页教材.html" air-pages/book.html

# 2. 重新拆分章节 docx（须用隔离 venv 解释器，它才带 python-docx）
C:/Users/sghpe/.workbuddy/binaries/python/envs/default/Scripts/python.exe split_for_feishu.py
cp "飞书导入/AR/"*.docx air-pages/chapters/

# 3. 提交并推送，GitHub Actions 自动部署
git -C air-pages add -A
git -C air-pages commit -m "更新教材内容"
git -C air-pages push
```

## 部署方式

GitHub Actions 自动部署，推送到 `main` 分支即触发。

> 仓库 **Settings → Pages → Build and deployment → Source** 已设为 **GitHub Actions**。
