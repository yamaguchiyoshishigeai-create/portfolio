# chatgpt-ops-rules 中枢参照方針

## 1. 目的

本書は、portfolioリポジトリにおける共通運用ルールの参照先を明確化するための文書である。

共通運用ルールの正本は、`yamaguchiyoshishigeai-create/chatgpt-ops-rules` とする。

本リポジトリには、公開ポートフォリオ固有の掲載方針、公開安全性方針、静的サイト仕様、GitHub Pages公開前提、Works掲載方針、改善タスク管理を残す。

## 2. 正本の分離

| 区分 | 管理場所 |
|---|---|
| 共通運用ルール | `yamaguchiyoshishigeai-create/chatgpt-ops-rules` |
| portfolio固有の掲載方針 | `portfolio` |
| portfolio固有の公開安全性方針 | `portfolio` |
| portfolio固有の静的サイト仕様 | `portfolio` |
| GitHub Pages公開前提 | `portfolio` |
| Works掲載方針 | `portfolio` |
| 改善タスク個票 | 対象作業が属するリポジトリ |

## 3. 作業開始時の参照順

portfolioの作業開始時は、以下の順に確認する。

1. Memory上のプロジェクト運用ルール。
2. `chatgpt-ops-rules` の `PROJECT_START_PROMPT.md`。
3. `chatgpt-ops-rules` の横断運用規程入口。
4. portfolio側の `PROJECT_START_PROMPT.md`。
5. portfolio側の `README.md`。
6. portfolio側の `docs/README.md`。
7. portfolio側の改善タスク課題一覧。
8. portfolio固有の企画、要件、設計、公開安全性文書。

## 4. 衝突時の優先順位

共通運用ルールとportfolio側文書に矛盾がある場合は、原則として `chatgpt-ops-rules` を優先する。

ただし、以下はportfolio側文書を正とする。

- 公開ポートフォリオとしての掲載方針。
- 個人情報・守秘情報・実企業名・顧客名の非掲載方針。
- HTML / CSS / JavaScript による静的サイト仕様。
- GitHub Pages公開前提。
- Works掲載方針。
- portfolio固有の改善タスク管理。

## 5. portfolio側に残す事項

以下はportfolio側に残す。

- 公開ポートフォリオとしての目的と対象読者。
- 掲載可否の判断基準。
- 履歴書、スキルシート、住所、電話番号、生年月日、実企業名、顧客名、内部システム名、守秘情報を配置しない方針。
- GitHub Pages公開前提。
- HTML / CSS / JavaScript による静的サイト仕様。
- Worksカードや公開制作物の掲載方針。
- portfolio側改善タスク課題一覧と個票。

## 6. portfolio側に重複保持しない事項

以下の共通運用ルール本文は、portfolio側へ重複コピーしない。

- ChatExec / ChatExec2方式の一般規程。
- ChatExec2 Python単一ファイル方式。
- ChatExec2 worktree分離実行方針。
- 通常PR自動merge方針。
- 個票先行main反映ゲート。
- Codex投入前ハンドオフゲート。
- 安全チェック発生時の仕様不変切替方針。
- 発生・残存課題の個票化最優先ルール。
- 実行計画と実行指示の分離方針。

必要な場合は、portfolio側に本文を再掲せず、`chatgpt-ops-rules` の該当規程を参照する。

## 7. 関連文書

- `PROJECT_START_PROMPT.md`
- `README.md`
- `docs/README.md`
- `docs/00_プロジェクト管理/02_改善タスク管理/改善タスク課題一覧.md`
