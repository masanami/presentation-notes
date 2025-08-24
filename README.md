# プレゼンテーション資料

このリポジトリは個人的なプレゼン資料を管理するためのリポジトリです。
スライド作成には [Marp](https://github.com/marp-team/marp-cli) を利用しています。

## 概要

Marpを使用してMarkdownからプレゼンテーションスライドを生成・管理するリポジトリです。

## ディレクトリ構成

```
presentation-notes/
├── README.md              # このファイル
├── package.json           # Marpビルド設定
├── .gitignore            # Git除外設定
└── presentations/         # プレゼンテーション資料
    └── sample-presentation/  # サンプルプレゼンテーション
        ├── slides.md         # Marpスライド（ソース）
        └── slides.html       # 生成されたHTML（自動生成）
```

## セットアップ

### 1. 依存関係のインストール

```bash
npm install
```

### 2. VSCode拡張機能（推奨）

VSCodeを使用している場合は、Marp for VS Code拡張機能をインストールすると、リアルタイムプレビューが可能です。

## 使用方法

### 新しいプレゼンテーションの作成

1. `presentations/`ディレクトリに新しいフォルダを作成
2. `slides.md`ファイルを作成し、Marp形式でスライドを記述
3. ビルドコマンドを実行してHTMLを生成

### スライドのビルド

```bash
# 全てのプレゼンテーションをビルド
npm run build

# 特定のプレゼンテーションをビルド
npm run build:sample

# ウォッチモード（自動ビルド）
npm run watch

# PDFとして出力
npm run pdf:sample

# PowerPointとして出力
npm run pptx:sample
```

### PowerPoint (PPTX) への変換

```bash
# PowerPointファイル（.pptx）として出力
npm run pptx:sample

# 全てのプレゼンテーションをPowerPointに変換
npm run pptx:all
```

生成されたPPTXファイルはMicrosoft PowerPoint、Keynote、Google Slidesなどで開けます。

### Marp記法の基本

```markdown
---
marp: true
theme: default
paginate: true
---

# スライドタイトル

スライドの内容

---

# 次のスライド

- 箇条書き
- リスト項目
```

## Marpテーマ

利用可能なテーマ:
- `default` - デフォルトテーマ
- `gaia` - Gaiaテーマ
- `uncover` - Uncoverテーマ

## リソース

- [Marp公式ドキュメント](https://marp.app/)
- [Marp CLIドキュメント](https://github.com/marp-team/marp-cli)
- [Markdownチートシート](https://marpit.marp.app/markdown)

## ライセンス

プロジェクトに応じて設定