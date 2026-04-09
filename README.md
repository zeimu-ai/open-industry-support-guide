# open-industry-support-guide

**AI活用に積極的な税理士（freee × Claude/ChatGPT ユーザー）向け**

金融庁『業種別支援の着眼点』（全135頁・10業種）をMarkdown + JSON形式に変換したデータセットです。AIエージェントやMCPと組み合わせて、月次面談・経営支援・事業性評価に活用できます。

## 対象業種

| # | 業種 | Markdown | JSON | ページ |
|---|------|----------|------|-------|
| 1 | 飲食業 | [industries/01-food-service.md](industries/01-food-service.md) | [data/01-food-service.json](data/01-food-service.json) | P.15-23 |
| 2 | 小売業 | *Phase 2* | *Phase 2* | P.24-32 |
| 3 | 卸売業 | *Phase 2* | *Phase 2* | P.33-39 |
| 4 | 建設業 | *Phase 2* | *Phase 2* | P.40-49 |
| 5 | 製造業 | *Phase 2* | *Phase 2* | P.50-62 |
| 6 | 運送業 | *Phase 2* | *Phase 2* | P.63-70 |
| 7 | サービス業 | *Phase 2* | *Phase 2* | P.71-77 |
| 8 | 医療業（小規模クリニック） | *Phase 2* | *Phase 2* | P.78-85 |
| 9 | 介護業 | *Phase 2* | *Phase 2* | P.86-97 |
| 10 | 宿泊業 | *Phase 2* | *Phase 2* | P.98-108 |

## 使い方

### AIとの活用（Claude / ChatGPT / Gemini）

1. 業種別mdファイルをAIに読み込ませる
2. 顧問先の試算表データ（freee等）と突き合わせる
3. 業種別の着眼点に基づいた対話・分析を行う

### freee MCP + Claude での実践例

```
1. freee MCPで当月の売上・原価・人件費を取得
2. 業種別の着眼点md（例: 01-food-service.md）を参照
3. 「FL比率が業界目安の60%を超えていますが、
    原価と人件費どちらから手をつけますか？」
    という対話ができる
```

（参考: 米世毅氏 [@TakeshiYonese](https://x.com/TakeshiYonese) のワークフロー）

### AIエージェント向け（JSON）

`data/` ディレクトリのJSONファイルは、AIエージェントが構造化データとして読み込む用途に最適化されています。

```bash
# 例: jqで飲食業のFL比率目安を取得
cat data/01-food-service.json | jq '.key_metrics[] | select(.name == "FL比率")'
```

### プロンプトテンプレート

`templates/` ディレクトリに、すぐに使えるプロンプトテンプレートを用意しています。

- [月次面談準備テンプレート](templates/monthly-review.md)

## ファイル構成

```
industries/   # 人間向けMarkdown（税理士が読む用）
data/         # AIエージェント向けJSON（Agent 3等が読み込む用）
templates/    # プロンプトテンプレート
appendix/     # コンセプト・用語集等
```

## 著作権・ライセンス

### 利用根拠

本データは以下の3重の根拠に基づき、適法に公開しています。

1. **金融庁ウェブサイト利用ルール**: 公共データ利用規約（PDL1.0）準拠で自由利用可（翻案含む、商用利用可）
2. **PDL1.0はCC BY 4.0互換**: クリエイティブ・コモンズ 表示 4.0 国際と互換性あり
3. **PDF資料P.131の明示的許可**:

> 「データを自由に加工できるため、組織・個人の着眼点の追加等のカスタマイズ、用途に応じた内容の追加、組織オリジナルの研修資料の作成 等に活用できます」

### 出典

- **資料名**: 『業種別支援の着眼点』～事業性の理解と経営改善の視点～
- **発行元**: 金融庁
- **発行日**: 2026年3月
- **原本URL**: https://www.fsa.go.jp/policy/chuukai/gyousyubetu.html
- **利用規約**: https://www.fsa.go.jp/rules/

### 改変の記載

本データはPDF原本をMarkdown + JSON形式に変換したものです。テキストのみを抽出し、画像・イラストは含みません。正確な情報は金融庁の原本をご確認ください。

## ライセンス

[CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)（クリエイティブ・コモンズ 表示 4.0 国際）

## 注意事項

- 本データは参考情報であり、正確性を保証するものではありません
- 最新の情報は金融庁の原本を必ず確認してください
- 業種別の数値・指標は調査時点のものです
