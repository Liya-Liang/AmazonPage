# FBA 售后功能顾问页

面向 FBA 卖家的顾问式说明页，介绍 BI、Parts、Partial Refund、Proactive MFI Claim 四大售后功能。

在线访问（GitHub Pages）：
`https://liya-liang.github.io/AmazonPage/fba-advisor-page/`

## 本地运行

直接用 Python 启动静态服务器：

```bash
cd /tmp/github/AmazonPage/fba-advisor-page
python3 -m http.server 8080
```

然后浏览器打开 `http://localhost:8080`

> 不需要 Python 也行，用任意静态服务器均可，例如：
> ```bash
> npx serve .
> # 或
> python -m http.server 8080
> ```

## 打包分发

整个 `fba-advisor-page/` 目录压缩为 zip 即可分发，页面不依赖后端，可直接本地打开。

## 资料下载说明

页面下载区已改为项目内相对路径：
- `assets/returns-guide.pdf`
- `assets/proactive-mfi-claim.docx`

## RAG 客服接入

页面已内置右下角 `RAG 客服` 组件。默认不会请求后端，需要先配置接口地址：

在 `index.html` 中找到：

```html
window.RAG_CHAT_CONFIG = {
  endpoint: "",
  headers: {},
  timeoutMs: 20000
};
```

将 `endpoint` 改为你的后端地址（例如 `https://api.example.com/rag/chat`）。

前端会 `POST` JSON：

```json
{
  "question": "用户输入问题",
  "page_path": "/AmazonPage/fba-advisor-page/",
  "page_title": "页面标题",
  "session_id": "rag-xxxx",
  "history": [{"role":"user","content":"..."}]
}
```

后端可返回任一字段用于展示答案：`answer` / `output` / `message` / `output_text`，或 OpenAI 风格 `choices[0].message.content`。

## 技术栈

- 单 HTML 文件，内联 CSS + JS
- 无框架依赖
- 字体：Amazon Ember（Google Fonts CDN）
- 图标：内联 SVG
- 响应式：支持桌面和移动端
