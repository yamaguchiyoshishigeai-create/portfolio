# CIポーリング終了条件固定方針

## 1. 目的

本書は、portfolioリポジトリでGitHub Actions、Preview、外部確認処理などの完了待ちを行う際に、ChatGPTがどの状態を終了条件として扱うかを定義する。

目的は、`queued`、`in_progress`、一部Job successなどの途中状態を完了扱いし、PR mergeや次タスクへ進む判断を誤ることを防ぐことである。

---

## 2. 終了条件ではない状態

以下は終了条件ではない。

- workflow run が `queued`。
- workflow run が `in_progress`。
- 一部Jobだけがsuccess。
- 一部Stepだけがsuccess。
- Post処理中。
- mergeability確認中。
- Previewや外部確認が未完了。

これらの状態では、原則としてポーリングを継続する。

---

## 3. 終了条件

以下のいずれかを終了条件とする。

| 状態 | 扱い |
|---|---|
| 全必須Jobが success | `CI_GREEN` として後続工程へ進める |
| failure | 失敗ログ確認、原因切り分け、修正方針提示へ進む |
| cancelled | 中止理由を確認し、再実行または作業停止を判断する |
| timed_out | タイムアウト理由を確認し、再実行または作業分割を検討する |
| action_required | 必要な人間操作または権限確認を明示する |
| 取得不能 | API制約、権限、認証、対象SHA誤りを確認する |
| ユーザー割り込み | ユーザー指示を優先する |
| 異常長時間化 | 状態、run番号、再開時確認事項を明示して扱う |

---

## 4. portfolioでの追加確認

portfolioは公開ポートフォリオ用リポジトリであるため、CI successだけで公開安全性確認を省略してはならない。

PR確認では、必要に応じて以下も確認する。

- 公開ページの表示崩れがないこと。
- リンクが壊れていないこと。
- 住所、電話番号、生年月日、年齢、履歴書原本、スキルシート原本が追加されていないこと。
- 実企業名、顧客名、内部システム名、守秘義務に触れる詳細仕様が追加されていないこと。
- APIキー、アクセストークン、秘密情報、環境変数ファイル、秘密鍵、個人情報が追加されていないこと。

---

## 5. CI_GREEN後の扱い

`CI_GREEN` は、CIまたは必要確認がsuccessであることを示す状態であり、単独では `DONE` ではない。

`DONE` とするには、以下が必要である。

1. mainへmerge済みであること。
2. 必要な課題管理整理が完了していること。
3. merge後のremote branch cleanupが完了していること。
4. local pruneが完了していること。
5. local main syncが完了していること。
6. 作業ブランチやremote tracking branchの残存が確認されていないこと。

---

## 6. 報告ルール

CI確認中は、途中状態と完了状態を分けて報告する。

例:

- `checks` はsuccessだが、`preview` はin_progressのためCI_GREENではない。
- 全必須JobがsuccessになったためCI_GREEN。
- CI_GREENだが、main未mergeのためDONEではない。
- main merge済みだが、cleanup/local sync未完了のためDONEではない。
