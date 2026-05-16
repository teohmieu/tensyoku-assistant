# 転職学習助手 📖

転職活動中に記事・インタビューを効率よく読み、AI対話で知識を定着させるためのWebツールです。

## 機能

- **音声読み上げ** — Web Speech API による日本語 TTS（文ごとに高亮表示）
- **章節ナビゲーション** — セクションチップをクリックして任意の箇所へジャンプ
- **AI対話 3モード**
  - Q&A — 記事内容について自由に質問
  - 面接RP — 面接官として質問・フィードバック
  - 解説 — 語彙・概念をわかりやすく説明
- **キーワード一覧** — 記事ごとの重要語彙を表示

## セットアップ

### 方法1：GitHub Pages（無料・最速）

1. このリポジトリを Fork または Clone
2. **Settings → Pages → Source: `main` branch → `/root`** に設定
3. `https://あなたのID.github.io/tensyoku-assistant/` でアクセス可能

### 方法2：Vercel（推奨）

1. [vercel.com](https://vercel.com) でGitHubアカウントと連携
2. "New Project" → このリポジトリを選択 → Deploy
3. 自動でURLが発行される

## 使い方

1. ページ上部の入力欄に **Anthropic API Key**（`sk-ant-...`）を入力して「保存」
2. 左のリストから記事を選択
3. ▶ ボタンで音声再生開始
4. 右パネルでAIと対話

> API Keyはブラウザの `localStorage` にのみ保存されます。サーバーには送信されません。

## 記事の追加方法

`index.html` の `ARTICLES` 配列に以下の形式でオブジェクトを追加してください：

```javascript
{
  id: 4,
  tag: 'インタビュー',
  badgeClass: 'badge-interview', // badge-interview / badge-news / badge-analysis
  title: '記事タイトル',
  subtitle: 'サブタイトル',
  meta: { source: '出典', date: '2024年4月', readTime: '約5分' },
  vocab: [
    { jp: '用語', reading: 'よみかた', def: '説明' }
  ],
  sections: ['セクション1', 'セクション2'],
  content: [
    { type: 'section', text: 'セクション見出し' },
    { type: 'p', sentences: ['文1。', '文2。', '文3。'] }
  ]
}
```

## 技術スタック

- 純粋な HTML / CSS / JavaScript（フレームワーク不要）
- Web Speech API（TTS）
- Anthropic Claude API（AI対話）
