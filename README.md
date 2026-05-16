# 転職学習助手 v3

## 架构说明

```
tensyoku-assistant/
├── index.html        # 前端页面
├── api/
│   ├── claude.js    # Anthropic API 中转（API Key 在服务器）
│   └── tts.js       # Google TTS API 中转
└── vercel.json       # Vercel 配置
```

API Key 存储在 Vercel 环境变量中，前端页面完全不包含任何密钥。

## 部署步骤

### 1. 推送到 GitHub
```bash
git add .
git commit -m "v3: Vercel backend proxy"
git push
```

### 2. 在 Vercel 设置环境变量

1. 打开 [vercel.com](https://vercel.com)，导入 GitHub 仓库
2. 进入项目 → **Settings → Environment Variables**
3. 添加以下两个变量：

| Name | Value |
|------|-------|
| `ANTHROPIC_API_KEY` | `sk-ant-...` |
| `GOOGLE_TTS_API_KEY` | `AIza...` |

4. 点击 **Redeploy** 使环境变量生效

### 3. Google Cloud 需要开启的 API

只需要 **Cloud Text-to-Speech API** 即可，已经足够。
在 Google Cloud Console 确认已开启：
- Cloud Text-to-Speech API ✓

### 4. 使用方法

- 🔗 左侧贴入文章 URL，AI 自动提取结构化内容
- 📝 或直接粘贴文章文本
- ▶ 播放按钮开始朗读（使用 Google TTS 自然语音）
- 🎭 朗读RP：役A/役B 用不同声音朗读
- 🎯 面接RP：面接官用语音提问，你用文字回答
- 💬 Q&A / 解説：AI 辅助理解文章内容
