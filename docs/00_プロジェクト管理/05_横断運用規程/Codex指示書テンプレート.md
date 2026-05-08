# Codex指示書テンプレート

## 1. 目的

本書は、portfolioリポジトリでCodexへHTML、CSS、データ、docs、確認手順、PR作成を依頼する際の標準テンプレートを定義する。

目的は以下である。

- Codex投入指示書の必須項目漏れを防ぐ。
- 公開安全性条件、対象ファイル、要求仕様、確認手順、Git公開Step、PR作成、未反映事項を一貫して扱う。
- `LOCAL_SUCCESS` と `DONE` の混同を防ぐ。
- 安全チェックやツール制約が発生しても、仕様と公開安全性条件を弱めずに別経路へ切り替えられるようにする。

---

## 2. 使用条件

このテンプレートは、以下の場合に使用する。

- HTML、CSS、データ、docsなど複数ファイルを修正する場合。
- 表示確認、リンク確認、公開安全性確認を伴う場合。
- commit、push、PR作成までCodexに到達させたい場合。
- ChatGPT(リポジトリ編集)の直接操作が安全チェックまたはツール制約で不安定な場合。

短い単一ファイル修正、局所的なdocs修正、README追記など、ChatGPT(リポジトリ編集)で安全に完了できる作業では、Codex投入前にその方が適切か確認する。

---

## 3. 指示書に必ず含める項目

Codex指示書には、少なくとも以下を含める。

1. 作業名と提案名。
2. 対象リポジトリ。
3. 最新 `main` からの新規クリーンブランチ方針。
4. モデル、インテリジェンス / reasoning effort、速度。
5. 安全チェックやツール制約を理由に要求仕様、文言、公開安全性条件を弱めない最重要制約。
6. 対象ファイル、確認対象、変更禁止対象。
7. 実施すること、実施しないこと。
8. 表示確認、リンク確認、公開安全性確認などの確認手順。
9. `git add`、`git commit`、`git push`、PR作成までのGit公開Step。
10. PR本文に含める内容。
11. 結果報告フォーマット。

---

## 4. 公開安全性制約

Codex指示書には、portfolio固有の公開安全性制約を必ず含める。

- 住所、電話番号、生年月日、年齢を配置しない。
- 履歴書原本、スキルシート原本を配置しない。
- 実企業名、顧客名、内部システム名、守秘義務に触れる詳細仕様を配置しない。
- APIキー、アクセストークン、秘密情報、環境変数ファイル、秘密鍵、個人情報を配置しない。
- 公開安全性のために削除または抽象化が必要な場合は、削除理由と影響範囲を明示する。

---

## 5. Git公開Step

Codexへ依頼する場合は、原則として以下を明記する。

1. `git status` で作業ブランチと変更ファイルを確認する。
2. 指定対象ファイルのみを `git add` する。
3. commit を作成する。
4. 作業ブランチを remote へ push する。
5. GitHub PR を作成する。
6. PR番号、commit SHA、変更ファイル、確認結果、CI状態、未反映事項を報告する。

Commit未作成、remote push未実施、PR未作成のいずれかが残る場合は、STATUSを `SUCCESS` または `DONE` にしてはならない。

---

## 6. 完了条件

- 最新 `main` 由来の作業ブランチで修正されている。
- 指定仕様が弱められずに反映されている。
- 公開安全性条件が維持されている。
- 対象ファイルのみが変更されている、または追加変更理由が明記されている。
- 必要な表示確認、リンク確認、またはCI確認が成功している。
- commit が作成されている。
- remote branch へ push されている。
- PR が作成されている。
- 未反映事項が none または明示されている。

---

## 7. 結果報告フォーマット

```text
JOB_ID:
STATUS: LOCAL_SUCCESS | COMMITTED | PUSHED | PR_READY | CI_GREEN | DONE | FAIL | PARTIAL | BLOCKED
Repository:
Branch:
Commit:
Remote Push: DONE | NOT_DONE | BLOCKED
PR: #number | NOT_CREATED | BLOCKED
Local Check:
CI:
Changed Files:
Public Safety Check:
Requirement Mapping:
Unreflected Items:
Blocking Point:
Next Required Action:
```

`PR: NOT_CREATED` または `Remote Push: NOT_DONE` の場合、`STATUS: DONE` または `STATUS: SUCCESS` として扱わない。

---

## 8. PR未作成時の追補指示

前回作業が仕様反映と確認手順までは完了していても、PR未作成、Commit未作成、またはremote push未実施の場合は、運用上は未完了として扱う。

その場合、ユーザー手作業へ直行せず、同じ作業ツリーで以下をCodexへ追補指示する。

1. 現在の変更内容を確認する。
2. 対象ファイルのみをstageする。
3. commitを作成する。
4. 作業ブランチをremoteへpushする。
5. GitHub PRを作成する。
6. PR作成が安全チェック、権限、CLI、remote、認証、GitHub連携制約で失敗した場合は、仕様を変更せず、どの段階で失敗したかを未反映として報告する。
7. 成功後、PR番号、commit SHA、変更ファイル、確認結果、未反映事項を報告する。

---

## 9. 関連規程

- `00_運用ルール索引と実行ゲート.md`
- `安全チェック発生時の仕様不変切替方針.md`
