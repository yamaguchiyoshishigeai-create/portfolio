# 表示確認スクリーンショット

このディレクトリは、公開ポートフォリオの主要表示状態を確認・説明するためのスクリーンショットを配置する場所です。

## 位置づけ

スクリーンショットは、ポートフォリオ本体を飾るための画像ではありません。主な用途は以下です。

- 応募・面談時に確認してほしい画面を説明する
- GitHub README上で主要改善点を短時間で伝える
- 公開前後の表示崩れ確認に使う
- 将来のUI変更時に、比較基準として使う

## 配置ルール

- 画像は `docs/screenshots/` 直下に配置する
- ファイル名は半角英数字、ハイフン、小文字を基本にする
- 形式は原則として `.png` とする
- 個人情報、住所、電話番号、非公開情報、未公開の企業名・顧客名が写り込まないことを確認する
- 画像を追加した場合は、README.md の「表示確認スクリーンショット」セクションから相対パスで参照する

## 推奨ファイル名

| ファイル名 | 対象画面 | 目的 |
|---|---|---|
| `top-hero.png` | トップページ hero | 第一印象と職務軸の確認 |
| `top-value-proposition.png` | トップページ Value Proposition | 業務改善・品質レビュー・AI活用設計支援の3軸確認 |
| `works-q-scout-business-value.png` | Q-Scout 詳細 | Springレビュー支援の実務価値確認 |
| `works-apim-business-value.png` | APIM 詳細 | API/MCP設計生成とAI実装指示への接続確認 |
| `career-representative-summary.png` | Career 詳細 代表案件サマリー | 代表案件4領域の確認 |
| `career-timeline-tags.png` | Career 詳細 主要職務経歴 | 業務領域・担当役割・主要技術タグの確認 |

## 撮影時の確認観点

1. ローカルまたはGitHub Pagesで対象ページを開く
2. ブラウザ幅は通常のデスクトップ幅を基本にする
3. 文字が読める倍率で撮影する
4. 個人情報・非公開情報の写り込みがないことを確認する
5. ファイル名を推奨ルールに合わせる
6. README.mdから相対パスで参照できることを確認する

## README掲載例

```markdown
### Top / Value Proposition

![Top Value Proposition](docs/screenshots/top-value-proposition.png)

### Works / Q-Scout Business Value

![Q-Scout Business Value](docs/screenshots/works-q-scout-business-value.png)

### Career / Timeline Tags

![Career Timeline Tags](docs/screenshots/career-timeline-tags.png)
```

## 今後の運用

初回は、表示確認資料として必要な画面だけを追加します。全ページを網羅することよりも、応募・面談で説明価値の高い画面を優先します。
