# portfolio 作業開始プロンプト

この文書は、`portfolio` リポジトリの新規チャット開始時または作業再開時に参照する入口文書である。

## 1. 共通運用ルール正本

共通運用ルールの正本は `yamaguchiyoshishigeai-create/chatgpt-ops-rules` とする。

作業開始時は、portfolio側文書だけでなく、先に `chatgpt-ops-rules` の `PROJECT_START_PROMPT.md` と横断運用規程入口を確認する。

## 2. portfolio側に残すもの

portfolio側には、以下の個別リポジトリ固有情報を残す。

- 公開ポートフォリオとしての掲載方針。
- 個人情報・守秘情報・実企業名・顧客名を配置しない公開安全性方針。
- GitHub Pages公開前提。
- HTML / CSS / JavaScript による静的サイト仕様。
- Works掲載方針。
- 企画、要件、設計、文言、データ構造。
- portfolio固有の改善タスク管理。

## 3. 作業開始時の確認順

1. Memory上のプロジェクト運用ルール。
2. `chatgpt-ops-rules` の `PROJECT_START_PROMPT.md`。
3. `chatgpt-ops-rules` の横断運用規程入口。
4. portfolio側の `PROJECT_START_PROMPT.md`。
5. portfolio側の `README.md`。
6. portfolio側の `docs/README.md`。
7. portfolio側の改善タスク課題一覧。
8. Open PRの有無。
9. 直前タスクのmerge、remote branch削除、worktree削除、local main同期、prune確認の完了状態。
10. portfolio固有の企画、要件、設計、公開安全性文書。

## 4. 衝突時の優先順位

共通運用ルールとportfolio側文書に矛盾がある場合、共通運用ルールは `chatgpt-ops-rules` を優先する。

ただし、公開ポートフォリオとしての掲載方針、個人情報・守秘情報・実企業名・顧客名の非掲載方針、静的サイト仕様、GitHub Pages公開前提、Works掲載方針はportfolio側文書を優先する。

## 5. ChatExec2標準

ChatExec2作業は、`chatgpt-ops-rules` の現行標準に従う。

原則として、Python単一ファイル方式を標準候補として扱う。

```text
ChatExec2_<JOB_ID>.py
```

結果ファイルは同じフォルダに以下として出力する。

```text
<JOB_ID>.summary.md
```

worktree配置は以下とする。

```text
<repo-parent>\<repo-name>-worktree\<JOB_ID>
```

作業完了後は、JOB_ID worktree削除、空の親worktreeフォルダ削除、`git worktree prune`、base repo main同期、remote tracking branch prune確認まで完了する。
