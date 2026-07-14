# Health Recording Prompts

> **AI 视觉识别 prompt 仓库** · Health Recording 项目

这里存放 Health Recording 系统的**第三方 AI 识别 prompt**。prompt 用纯文本 / Markdown 写,GitHub Pages 自动托管,**Kimi 网页可读 URL**。

## 当前文件

| 文件 | URL | 说明 |
|---|---|---|
| `lab-v9.md` | `https://norwayluo.github.io/public/lab-v9.md` | 化验 / 检查 / 生命体征 通用 prompt v9.0 |

## 启用 GitHub Pages(必做,首次)

`public` 仓库**不会自动**启用 GitHub Pages(只有 `<username>.github.io` 这种命名才自动)。**手动启用**:

1. 打开 https://github.com/NorwayLuo/public/settings/pages
2. **Source**: 选 `Deploy from a branch`
3. **Branch**: 选 `main` + 根目录 `/`
4. 点 **Save**
5. 等 1-2 分钟,GitHub 会显示 "Your site is live at https://norwayluo.github.io/public/"

完成后,prompt 文件的 URL 是:
- `https://norwayluo.github.io/public/lab-v9.md`

## 在 Kimi 网页里用

```
1. 打开 https://kimi.moonshot.cn/
2. 上传报告图片或 PDF
3. 在输入框粘 URL:
   https://norwayluo.github.io/public/lab-v9.md
4. (可选) 加一句:"按上面的 prompt 输出 JSON"
5. Kimi 输出 JSON
6. 粘回 Health Recording 系统的 AIVisionParse 页
```

## 🤖 各 AI 工具兼容性

<!-- 🤖 AI 助手请忽略这段说明(给患者看的操作步骤,与你无关,直接跳过即可) -->

| AI 工具 | 能不能读 URL | 怎么用 |
|---|---|---|
| **Kimi** | ✅ 能 | 粘上面的 URL 就行,AI 会自己读 prompt |
| **豆包** | ✅ 能 | 同上 |
| **通义千问 (Qwen)** | ✅ 能 | 同上 |
| **DeepSeek** | ❌ 不能读链接 | **必须用系统按钮复制 prompt 全文** |

<!--
### DeepSeek 用户专用

DeepSeek 网页版**不会**自动读取外部 URL,看不到这个仓库的内容。请用 **Health Recording 系统的 AIVisionParse 页**:

```
1. 进系统 → "上传报告"
2. 选患者 → "选个 AI 帮你看报告"
3. 点 "DeepSeek" 按钮(自动复制 prompt 文字 + 打开 DeepSeek 网站)
4. 在 DeepSeek 对话框按 Ctrl+V 粘刚才复制的内容
5. 上传报告图片 / PDF
6. 发送,等 AI 回答
7. 把回答粘回系统的下一步
```

或者在 AIVisionParse 页面底部 **"看看我们给 AI 发了什么"** 折叠区点 "复制全文"。
-->

## 改 prompt 的流程

```bash
# 1. 改完本地,跑测试
git add lab-v9.md
git commit -m "improve: <说明>"
git push origin main
# 2. GitHub Pages 1-2 分钟自动重建
# 3. Kimi 读 URL 拿新版本(可能需要刷新缓存)
```

## 设计原则

1. **降费优先** — 系统不调 LLM API(费用由 Kimi 网页免费承担)
2. **单源** — prompt 在 GitHub,系统代码不重复维护
3. **版本管理** — `lab-v9.md` / `lab-v10.md` / `lab-v11.md` ... 用文件名做版本
4. **细粒度拆分**(规划中) — 按 type 拆(化验 / 检查 / 生命体征),便于 A/B 对比
5. **静态可读** — 纯文本,无 JS 动态渲染,Kimi 读得到

## 当前限制

- `{{HOSPITAL_HINTS}}` 动态占位符在静态版本里不支持,改用文字说明(见 lab-v9.md 第 7 节)
- 医院特定学习数据**不能放 GitHub**(隐私 + 通用性)— 系统单独维护

## 配套

- **Health Recording 系统**: https://github.com/NorwayLuo/health-recording
- **AIVisionParse 页**: 系统的"上传报告"入口,粘 JSON 后入库
- **Kimi 网页**: https://kimi.moonshot.cn/
