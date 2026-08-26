# CISpir インストール・操作ガイド

**CISpir** は、YouTube の字幕を Anki の学習カードに変換する Chrome 拡張機能です。音声・AI 翻訳・文法解析つきで、ローカルの Anki に直接保存します。

## 🚀 クイックスタート

1. [Anki デスクトップ版](https://apps.ankiweb.net/) をインストール（Web / モバイル版は不可）
2. Anki に **AnkiConnect** アドオンを追加（コード `2055492159`）
3. **CISpir** をインストール（`dist` フォルダを読み込む）
4. （任意）設定で **AI API キー** を登録
5. YouTube 動画を開く → CISpir アイコン → 字幕を読み込み → ☆ で Anki に保存

## 必要なもの

- Windows / macOS / Linux
- Chromium 系ブラウザ（Chrome 114+ / Edge / Brave / Arc）
- Anki デスクトップ版
- （任意）AI API キー

## 1. Anki（デスクトップ版）をインストール

- ダウンロード: https://apps.ankiweb.net/
- **デスクトップ版が必須**です。AnkiWeb やモバイル版は AnkiConnect に非対応です。

## 2. AnkiConnect をインストール

1. Anki を開く
2. ツール → アドオン → アドオンを取得…
3. `2055492159` を入力 → OK
4. Anki を再起動
5. 確認: `http://localhost:8765` を開き、`{"result": null, "error": "must be a POST request"}` と表示されれば OK

## 3. CISpir をインストール

**方法A — Chrome ウェブストア**（近日公開）: 「CISpir」を検索 → Chrome に追加。

**方法B — 展開した拡張機能を読み込む（現在のおすすめ）:**

1. `github.com/smith0814666/CISpir-anki-extenstion/releases` から最新の ZIP をダウンロード
2. 解凍する
3. `chrome://extensions/` を開く → **デベロッパーモード** をオン
4. **パッケージ化されていない拡張機能を読み込む** → `dist` フォルダを選択

📌 ピン留め: パズルアイコン → CISpir → 📌。

## 4. AI を設定（任意）

いずれか 1 つを選び、CISpir 設定（⚙ → Save）にキーを貼り付けます。

| プロバイダ | キー取得 URL | デフォルトモデル |
|---|---|---|
| Google AI | aistudio.google.com/apikey | gemini-2.0-flash（無料枠あり） |
| DeepSeek | platform.deepseek.com/api_keys | deepseek-chat |
| OpenAI | platform.openai.com/api-keys | gpt-4o-mini |
| Anthropic | console.anthropic.com/keys | claude-sonnet-5-20251001 |

🔒 キーは暗号化（AES-GCM）され、ブラウザ内にのみ保存されます。

## 5. 使い方

1. 字幕のある YouTube 動画を開く
2. Anki を起動しておく（サイドバーに 🟢 Anki ✓ と表示）
3. CISpir アイコンをクリックしてサイドパネルを開く
4. 字幕の言語と翻訳先の言語を選ぶ → **Load Captions**
5. 文をクリックすると再生、単語を選択すると翻訳が表示
6. **☆** をクリックして Anki に保存（音声・翻訳・文法・動画リンクを自動取得）

### 操作一覧

| 操作 | 方法 |
|---|---|
| 文を再生 | クリック |
| 前 / 次 | ⏮ ⏭ または ← → キー |
| 1 文ループ | 🔄 |
| 再生速度 | 0.5×〜2× |
| 単語を調べる | 選択（ドラッグ） |

### AI 機能

| 機能 | ボタン | 内容 |
|---|---|---|
| 全訳 | 🌐 | 字幕を一括翻訳 |
| 文法解析 | 📖 | 文法の分解・読み仮名 |
| チャンク抽出 | 🔤 | 学習に役立つ単語・フレーズを取り出して Anki に保存 |
| 動画要約 | 📄 | 要約・重要語彙・難易度 |

## Anki カードのフィールド

Text · Translation · Reading · Audio · TargetWord · WordReading · Definition · Explanation · Source

## 💝 寄付

CISpir は完全無料です。すべての機能を無料で使えます。役に立ったと感じたら、継続的な開発を自主的に支援できます。**寄付によって機能がアンロックされたり制限されたりすることはありません。**

サイドパネルまたは設定の **Support CISpir** ボタンから寄付できます。3 つの方法に対応しています：

| WeChat | Alipay |
|:---:|:---:|
| <img src="./assets/donation/wechat-qr.jpg" alt="WeChat 寄付 QR コード" width="200"> | <img src="./assets/donation/alipay-qr.jpg" alt="Alipay 寄付 QR コード" width="200"> |

> **PayPay**: PayPay で ID `milesmissyou` に送金（QR コードなし）。

決済は選択したアプリ内で行われます。CISpir が支払い情報を読み取ることはなく、端末データのアップロードも行いません。

## よくある質問

- **Anki ✗ と表示される?** Anki 起動中？ AnkiConnect 導入済み？ 再起動した？ `http://localhost:8765` を確認。
- **字幕が出ない?** ページを再読み込み。一部の動画はアクセス制限あり。
- **API キーなしでも使える?** 字幕・音声・保存は可。翻訳・文法・チャンク抽出・要約は不可。
- **対応ブラウザ?** Chrome / Edge / Brave / Arc ✅ · Firefox / Safari ❌。

## サポート

github.com/smith0814666/CISpir-anki-extenstion
