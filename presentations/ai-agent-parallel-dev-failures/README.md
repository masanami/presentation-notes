# Mermaid図の画像変換手順

## セットアップ（初回のみ）
```bash
npm install --save-dev @mermaid-js/mermaid-cli
```

## Mermaid図の作成と変換

1. **Mermaid図を作成**
   - `diagrams/` ディレクトリに `.mmd` ファイルとして保存
   - 例: `diagrams/development-flow.mmd`

2. **画像に変換**
   ```bash
   # 特定のプレゼンテーションの図を変換
   npm run mermaid:ai
   
   # または全てのMermaidファイルを一括変換
   npm run mermaid
   ```

3. **生成された画像を使用**
   - 画像は `img/` ディレクトリに保存される
   - スライドで `![](img/development-flow.png)` として参照

## 利用可能なコマンド

- `npm run mermaid` - 全てのMermaidファイルを画像に変換
- `npm run mermaid:ai` - AI並列開発プレゼンの図を変換

## 注意事項

- 図を更新した場合は、再度変換コマンドを実行してください
- 生成される画像は透明背景のPNG形式です