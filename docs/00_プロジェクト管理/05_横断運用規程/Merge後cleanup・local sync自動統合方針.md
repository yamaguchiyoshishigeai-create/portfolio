# Merge後cleanup・local sync自動統合方針

## 1. 目的

本書は、portfolioリポジトリでPRをmainへmergeした後のremote branch cleanup、local prune、local main syncを、必要に応じて1本のChatExec2スクリプトへ統合して実行する方針を定義する。

目的は、merge後に作業ブランチやremote tracking branchが残り、次タスクの起点や公開状態の判断が不明確になることを防ぐことである。

---

## 2. 基本方針

PRをsquash mergeした後は、以下を必須後続処理とする。

1. remote作業ブランチを削除する。
2. GitHub側で対象branchが残っていないことを確認する。
3. ローカルで `git fetch origin --prune` を実行する。
4. local main を `origin/main` にfast-forward同期する。
5. local work branch が残っている場合は削除する。
6. remote tracking branch が残っていないことを確認する。
7. current branch が `main` であることを確認する。
8. worktree がcleanであることを確認する。

---

## 3. 自動統合の原則

削除対象branch、対象リポジトリ、local sync対象パスが明確な場合、ChatGPTは確認待ちに戻らず、remote branch cleanup、local prune、local main syncを1本化したChatExec2スクリプト作成まで進める。

Windows向けスクリプトでは、原則として `.bat` または `.cmd` を使用し、以下を満たす。

- JOB_IDを含む一意なファイル名にする。
- 成功時に `[OK] <JOB_ID>_DONE` を表示する。
- 失敗時に `[FAIL] <JOB_ID>_FAILED` を表示する。
- 成功・失敗にかかわらず結果末尾を表示する。
- ウィンドウを保持する。
- 秘密情報、不要な個人情報、非公開情報を結果に含めない。

---

## 4. 完了条件

merge後cleanup・local syncは、以下を満たすまで完了扱いしない。

- 対象PRがmainへmerge済みであること。
- remote作業ブランチが削除済みであること。
- GitHub側branch検索で対象branchが0件であること。
- local pruneが完了していること。
- local mainが`origin/main`に追従していること。
- local main HEADが期待するmerge commitと一致していること。
- current branchが`main`であること。
- worktreeがcleanであること。
- local work branchが削除済みまたはabsentであること。
- remote tracking branchが削除済みまたはabsentであること。

---

## 5. 分割実行を許容する例外

以下の場合は、1本化せず分割実行してよい。

- 対象ローカルパスが不明な場合。
- ユーザーPC上で複数cloneが存在し、同期対象を特定できない場合。
- local worktreeがdirtyであり、先に退避判断が必要な場合。
- remote branch削除権限がない場合。
- GitHub API、gh CLI、git CLIの認証や権限が不安定な場合。

分割する場合でも、完了済み工程、未実施工程、次に必要な工程を明確に報告する。

---

## 6. portfolioでの注意

portfolioは公開ポートフォリオ用リポジトリであるため、cleanupやlocal syncの過程で、非公開情報を含むログやローカルファイルをPR、Issue、commitに含めてはならない。

ChatExec2結果を共有する場合は、必要最小限のサニタイズ済み結果に限定する。
