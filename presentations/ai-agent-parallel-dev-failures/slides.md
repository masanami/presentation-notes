---
marp: true
theme: gaia
paginate: true
backgroundColor: #f7fafc
style: |
  section {
    font-family: 'Helvetica Neue', Arial, 'Hiragino Sans', 'Meiryo', sans-serif;
    font-size: 26px;
  }
  h1 {
    color: #2b6cb0;
    font-size: 40px;
    font-weight: 700;
    margin-bottom: 0.5em;
  }
  h2 {
    color: #1a365d;
    border-bottom: 3px solid #4299e1;
    padding-bottom: 0.3em;
    font-size: 30px;
    margin-top: 0.5em;
  }
  ul {
    line-height: 1.6;
  }
  li {
    margin-bottom: 0.3em;
  }
  strong {
    color: #2c5282;
  }
  code {
    background: #e2e8f0;
    padding: 2px 6px;
    border-radius: 4px;
    font-size: 0.9em;
  }
  pre {
    background: #2d3748;
    padding: 1em;
    border-radius: 8px;
    font-size: 0.85em;
  }
  blockquote {
    border-left: 4px solid #4299e1;
    padding-left: 1em;
    color: #2d3748;
    font-style: italic;
  }
  .small {
    font-size: 0.7em;
  }
  .highlight {
    color: #3182ce;
    font-weight: bold;
    background: linear-gradient(transparent 60%, #bee3f8 60%);
  }
---

<!-- _class: lead -->
<!-- _paginate: false -->

<div style="display: flex; flex-direction: column; justify-content: center; align-items: center; height: 100%; text-align: center;">

<h1 style="font-size: 44px;">AIエージェント並列開発の<br>失敗体験と学び</h1>

<br>

**AI駆動開発勉強会 沖縄（第2回）**

波平真実（ナミヒラマサミ）

2025/08/26

</div>

---

# アジェンダ

1. **自己紹介** - AI駆動開発のモチベーション
2. **今回のチャレンジ** - 並列AI開発への挑戦
3. **期待値と現実のギャップ** - 想定外の問題
4. **失敗の内容** - 何が起きたか
5. **改善アプローチ** - 現在の取り組み
6. **学び** - 得られた知見

---

# 自己紹介

![bg right:30% fit](img/profile.png)

**波平真実（ナミヒラマサミ）**

- **株式会社ZENE** 遺伝子検査の会社
- テックリード（3〜4人の小規模チーム）
- **ゲノム解析ワークフロー・WEBアプリケーション開発**
  - 遺伝子診断システムの構築
- Claude CodeやCursorなどを普段使いしているが、使いこなせてはいない

**AI駆動開発のモチベーション**
 センシティブな情報を扱うため品質を担保は必須、その上でAI駆動開発の恩恵を受けて開発速度を上げたい


---

# 並列開発を行おうと思ったキッカケ

## Twitterで並列開発のツイートを拝見

- tmuxを使って複数エージェント同時実行するツイート
- 16ペインでエージェントがコミュニケーションをとりながら
  タスクを並列に処理する様子を見て面白そうと感じた。
- 実装速度が数倍になるのでは？という淡い期待

**→ 今回チャレンジしてみることに**

---

# 開発対象プロダクト

## ToB向け解析レポート進捗管理アプリケーション

新規開発予定のプロダクトのプロトタイプ

<div style="display: flex; justify-content: space-between;">
<div style="flex: 1;">

- **Next.js + AWSサーバレス構成**
- **主要機能**
  - ログイン / アカウント管理
  - 進捗管理
  - レポートファイル管理
  - 監査ログ

</div>
<div style="text-align: right;">

![width:300px](img/system_archtecture.png)

</div>
</div>

---

# エージェント構成

![bg right:40% fit](img/screen.gif)

## エージェント構成
- **リーダー × 1**：オーケストレーション担当
- **ワーカー × 3**：各機能の実装担当
- **利用ツール**：Claude Code + tmux
- **モデル**：Claude 4 Sonnet / Claude 4 Opus

---

# 開発フローのイメージ

![width:900px](img/development-flow.png)

**今回話す内容は並列実装の部分について**

---

# 期待していたこと

![bg right:45% contain](img/expected-gantt.png)

<br>

- **きれいに並列で進められる開発**
- **待ち時間もあまりなくスムーズ**
- **レビュー中も裏で次の実装が進む**
- **2-3回のやりとりでタスク完了**

---

# 実際に起きたこと

![bg right:45% contain](img/actual-gantt.png)

- **頻繁にブロッキングが発生**
  - 暴走しがちで不要な機能やあきらかにおかしい実装
  - 依存関係を無視した実装
  - 怖いので別タスクは待機させることも

- **レビュー疲れで処理が滞留**
  - 大量のPRを同時レビューは困難
  - 結果的に順番に処理

# **「直列の方が早くね？」**

---

# 失敗の内容：記憶喪失による混乱

## コンテキストウィンドウの限界
- 想定より早くコンテキスト上限に到達
- Auto Compactによる記憶喪失が頻発
- 設計と実装にズレが発生

## 連鎖的なカオス
- 後続タスクでもエージェントが間違った前提で実装
- エラー修正も表面的な対処のみ行われることも

# **プロトタイプなのに負債まみれ**

---

# 失敗の内容：（続き）

## エージェントの暴走
- スコープクリープ（勝手に機能追加）
- 開発原則を無視（YAGNI、DRY、KISS違反など）
- 同じような処理を重複して定義

## その他の問題
- レビュー地獄に陥り気力枯渇
- しっかりコードを見れないことがあり実装を忘れがち

# **ビジネスクリティカルな部分では責任が持てないという印象**

---

# うまくいった部分もある

## 並列でも成功した領域
- UIやデザインは並列でもうまくいくことが多かった
  - 一部コード重複があるくらい
- 非コア機能では十分な品質
- **動くものはなんだかんだ速く完成はする**

---

# 反省と改善

## 反省点
- **直列で十分な品質を担保するフローの整備が不十分**
- 人間の負荷が高く、そのままではうまくいきそうにない

## タスクごとの並列ではなく品質向上のための並列化
- **実装エージェントとレビューエージェントのペアプロ**
  - 設計に従って実装 / コーディング規約や整合性をチェック
- 別コンテキストで記憶喪失を防ぐ

<div class="small">

**※その他の施策案**
- 人間の処理能力を基準に並列度を調整
- その人の背景に応じたレビュー要約エージェントの追加 など

</div>

---

# 改善アプローチの効果

## 定性的な結果
- 体感的にコードの品質が向上
- **レビューのやりとりやCodeRabbitのコメントが半減**
- タスクサイズも適切に保たれPRの肥大化も防止

**まだ課題多いが方向性は良さそう**
- 人の負担を減らせている
- 普段の開発業務にも知見が活かせて好影響

---

# 体験を通した学び

## エージェント並列開発自体について
- **まずは直列のフローを整備して人間の負荷を下げることが重要**
- 余力を増やして徐々にスケールするとよさそう
- 並列化で工夫する余地はまだまだありそう

## 副次的な学び - これが結構大きい
- **エージェントを自律させてチーム開発させる試み**
  普段のAIの使い方にもまだまだ改善の余地があることに気づいた
- **普段の開発プロセス改善のきっかけ**
  少人数チームのため属人的な体制になりがちだったため、
  各開発フェーズについてうまく回る仕組みを考える良い機会になった

---

<!-- _class: lead -->
<!-- _paginate: false -->

<div style="display: flex; flex-direction: column; justify-content: center; align-items: center; height: 100%;">

# ご清聴ありがとうございました

</div>
