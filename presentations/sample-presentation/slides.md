---
marp: true
theme: gaia
paginate: true
backgroundColor: #fff
backgroundImage: url('https://marp.app/assets/hero-background.svg')
---

<!-- _class: lead -->

# Marpサンプルプレゼンテーション

## Markdownでスライドを作成

2025年8月24日

---

# アジェンダ

1. Marpとは？
2. 基本的な記法
3. レイアウトとスタイル
4. 画像とメディア
5. 高度な機能
6. まとめ

---

# Marpとは？

**Marp** (Markdown Presentation Ecosystem) は、Markdownからプレゼンテーションを作成するツールです。

## 主な特徴

- 📝 **シンプル**: Markdownで記述
- 🎨 **テーマ対応**: 複数のテーマから選択可能
- 📱 **レスポンシブ**: どのデバイスでも表示可能
- 🚀 **高速**: 軽量で高速な変換

---

# 基本的な記法

## 見出し

```markdown
# 見出し1
## 見出し2
### 見出し3
```

## リスト

- 項目1
- 項目2
  - サブ項目
  - サブ項目

---

# テキストの装飾

## 強調

- **太字**: `**太字**`
- *イタリック*: `*イタリック*`
- ~~取り消し線~~: `~~取り消し線~~`

## リンクとコード

- [リンク](https://marp.app/): `[リンク](URL)`
- `インラインコード`: `` `コード` ``

```javascript
// コードブロック
function hello() {
  console.log("Hello, Marp!");
}
```

---

# レイアウトとスタイル

<!-- _class: lead -->

このスライドは `lead` クラスを使用して中央配置されています。

```markdown
<!-- _class: lead -->
```

---

# 2カラムレイアウト

<div style="display: flex; gap: 2em;">
<div style="flex: 1;">

## 左カラム

- 項目1
- 項目2
- 項目3

</div>
<div style="flex: 1;">

## 右カラム

```python
def greet(name):
    return f"Hello, {name}!"

print(greet("Marp"))
```

</div>
</div>

---

# 画像の挿入

## 基本的な画像挿入

![w:600](https://via.placeholder.com/600x400)

```markdown
![w:600](image.jpg)
```

`w:600` で幅を指定できます

---

# 背景画像

<!-- _backgroundImage: "linear-gradient(135deg, #667eea 0%, #764ba2 100%)" -->
<!-- _color: white -->

## 背景画像の設定

このスライドはグラデーション背景を使用しています。

```markdown
<!-- _backgroundImage: "linear-gradient(...)" -->
<!-- _color: white -->
```

---

# 表の作成

| 項目 | 説明 | 価格 |
|------|------|-----:|
| Marp CLI | コマンドラインツール | 無料 |
| Marp for VS Code | VSCode拡張機能 | 無料 |
| Marp Core | コアライブラリ | 無料 |

---

# 数式の表示

## インライン数式

アインシュタインの有名な方程式: $E = mc^2$

## ブロック数式

$$
\frac{n!}{k!(n-k)!} = \binom{n}{k}
$$

---

# アニメーション

<!-- _class: lead -->

## Marpの特徴

- 🎯 **シンプル**
- ⚡ **高速**
- 🎨 **美しい**

各項目は順番に表示されます（プレゼンテーションモード時）

---

# 高度な機能

## カスタムCSS

```css
/* カスタムスタイル */
section {
  font-family: 'Noto Sans JP', sans-serif;
}

h1 {
  color: #4a5568;
  border-bottom: 2px solid #e2e8f0;
}
```

---

# プレゼンテーションのヒント

1. **シンプルに保つ**: 1スライド1トピック
2. **視覚的に**: 図表や画像を活用
3. **一貫性**: テーマとスタイルを統一
4. **練習**: プレゼンテーション前に練習

---

<!-- _class: lead -->

# まとめ

## Marpで効率的なプレゼンテーション作成

- ✅ Markdownで簡単記述
- ✅ バージョン管理可能
- ✅ 共同編集しやすい
- ✅ エクスポート形式豊富

---

<!-- _class: lead -->
<!-- _backgroundColor: #123 -->
<!-- _color: white -->

# ありがとうございました

## 質問・ご意見をお待ちしています

📧 your-email@example.com
🐦 @your-twitter
🌐 your-website.com