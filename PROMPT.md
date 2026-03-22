# Daily English アプリ 再生成プロンプト

## 概要

毎日15分で英語リスニング力を伸ばすWebアプリ。
ビルド不要のシングルHTMLファイル（React + Tailwind CDN）。

---

## プロンプト全文

```
下記の条件で毎日英語リスニング学習ができるWebアプリを1つのHTMLファイルで作成してください。
ビルドツール不要で、ブラウザでそのまま開けること（React・Babel・Tailwind等はCDN使用可）。

---

## ユーザー情報

- 英語レベル：映画字幕なしは難しい／ニュースは背景知識で対応可／ビジネス会議はトピックが分かれば対応できるが細かい表現が苦手
- 興味：日本のニュース・ビジネス英語
- 目標：リスニングを最優先で伸ばす

---

## 毎日15分の学習構成（4セクション）

### セクション1：語彙（5分）
- 日本のニュース・ビジネス関連の語彙 5語
- 各語彙：英単語・音声記号・日本語訳・カテゴリタグ（経済/IT/ESG等）・英語例文・日本語訳
- タップで展開するアコーディオン形式
- 各単語・例文の横に 🔊 ボタン（Web Speech API で読み上げ）
- 3問の語彙クイズ（4択）

### セクション2：リスニング（5分）
- 日本のニュースを題材にした英語スクリプト（約150語）
- **音声再生プレイヤー**（Web Speech API）：速度調整0.7x〜1.2x・文ごとにハイライト・文クリックで個別再生
- 穴埋め問題（空欄6〜10箇所）：ヒント付き・答え合わせ機能・正誤判定・スコア表示
- 理解クイズ3問（4択）
- 重要語彙リスト（折りたたみ式）

### セクション3：読解（5分）
- ビジネス会議シーンの英文（約150語）・改行で段落分け
- 語彙リスト（折りたたみ）
- 文法ポイント解説（折りたたみ）：パターン名・説明・例文3つ
- 理解クイズ3問（4択）
- 会議で使える表現3選：表現・使い方・例文

### セクション4：リスニングトレーニング（5分）
5つのステップをタブで切り替え：
1. **リピーティング**：音声再生プレイヤー＋スクリプト表示
2. **音読**：音声再生プレイヤー＋スクリプト表示
3. **ディクテーション**：音声再生プレイヤー＋テキストエリア（書き起こし用）＋答え確認ボタン
4. **オーバーラッピング**：音声再生プレイヤー＋スクリプト表示
5. **シャドーイング**：音声再生プレイヤー＋スクリプトはぼかし（クリックで表示）
- マイク録音ボタン（MediaRecorder API）：録音→再生でセルフチェック
- 各ステップに「完了」ボタン、完了数の進捗バー表示

---

## コンテンツデータ

以下のトピックで7日分用意する（日付に応じてローテーション）：
1. 日本の経済回復（fiscal year / stimulus package / stakeholder / sustainable growth / monetary policy）
2. テクノロジー・DX（digital transformation / cybersecurity / AI-driven / data breach / scalability）
3. 環境・ESG（carbon neutral / renewable energy / ESG criteria / greenhouse gas emissions / supply chain）
4. 人事・労働（workforce / remote work / retention rate / upskilling / diversity and inclusion）
5. 貿易・国際関係（trade deficit / tariff / free trade agreement / geopolitical risk / foreign direct investment）
6. 金融・投資（interest rate / portfolio / dividend / volatility / asset allocation）
7. 医療・社会保障（healthcare system / social security / telemedicine / demographic shift / preventive care）

---

## 共通UI・機能要件

### タイマー
- 各セクションに5分カウントダウンタイマー
- グレーの「⏱ タイマー開始」ボタン（音声再生ボタンと混同しないよう目立たせない）
- 残り60秒で黄色、残り30秒で赤くアニメーション

### 音声再生プレイヤー（ScriptPlayer）
- 青い枠・「🔊 音声再生プレイヤー」ヘッダーで音声と明確に区別
- 大きめの ▶ ボタン（影付き・紫系カラー）
- 速度：遅い(0.7x) / 普通(0.85x) / 速い(1.0x) / 最速(1.2x)
- 再生中は現在の文をハイライト、各文クリックで個別再生
- 「💡 各文をクリックして個別再生できます」の注釈

### クイズ共通
- 4択・選択後に正誤判定（正解を緑・不正解を赤）
- 最後にスコア表示（N/3 + パーセント）
- 「もう一度」ボタン

### 進捗管理
- 各セクション「✓ このセクションを完了にする」ボタン
- LocalStorageで完了状態・連続学習日数（ストリーク）を保存
- ヘッダーに今日の進捗ドット（4つ）と 🔥 連続日数バッジ
- 全セクション完了で「🎉 今日の学習完了！」バナー表示

### ナビゲーション
- 上部タブ（語彙/リスニング/読解/トレーニング）＋完了チェック表示
- 「← 前」「次 →」ボタンで日付コンテンツを切り替え

---

## デザイン要件

- フォント：Inter + Noto Sans JP（Google Fonts CDN）
- カラー：プライマリ #4f46e5（インディゴ）・セカンダリ #0ea5e9（スカイ）
- ヘッダー：グラデーション（インディゴ→バイオレット→スカイ）・sticky
- カード：白背景・角丸12px・薄いシャドウ・ボーダー
- アニメーション：fadeIn・pulse・shake（誤答時）・pop（正答時）
- レスポンシブ対応（スマホ/PC両対応）
- カスタムスクロールバー

---

## 技術スタック

- React 18（CDN: unpkg）
- Babel Standalone（JSX変換）
- Web Speech API（SpeechSynthesis）：音声読み上げ
- MediaRecorder API：マイク録音
- localStorage：進捗・ストリーク保存
- CSS カスタムプロパティ（CSS変数）でテーマ管理
- 外部依存なし（Google Fontsのみ）
```

---

## 補足メモ

### 注意点
- タイマーボタンは**グレー・地味**にする（音声の ▶ と混同されやすい）
- 音声プレイヤーは**青枠・ヘッダーラベル付き**で目立たせる
- Web Speech API は `lang = 'en-US'`、`rate = 0.85`（デフォルト）を指定

### よく使う表現パターン（Reading セクション）
- 数値＋比較：`increased by X% compared to last year`
- 問題提起：`The main bottleneck appears to be...`
- 解決提案：`To address this, I propose...`
- 選択肢提示：`We have two options: either A or B`
- 意見募集：`Does anyone have concerns about this approach?`

### ファイル構成
```
english-daily/
└── index.html   （すべて1ファイルに収める）
```

### GitHub Pages への公開手順
```bash
git init
git add index.html
git commit -m "Initial commit"
git remote add origin https://github.com/<USERNAME>/<REPO>.git
git branch -M main
git push -u origin main
# GitHub → Settings → Pages → Branch: main / root → Save
```
