# portfolio

山口能成の公開ポートフォリオ用リポジトリです。

公開URL: https://yamaguchiyoshishigeai-create.github.io/portfolio/

このリポジトリでは、長期のシステム開発経験を基盤に、AI/Web領域への再接続を示す職務経歴型ポートフォリオを管理します。

## 初期方針

- 静的サイトとして構成する
- GitHub Pagesでの公開を想定する
- 履歴書・スキルシート原本や個人情報は配置しない
- 実企業名・顧客名・内部システム名は公開向けに抽象化する
- 改善タスクは `TSK-###` で管理する

## サイト構成

- `index.html`: 公開ポートフォリオ本体
- `assets/css/style.css`: サイトスタイル
- `assets/js/main.js`: 最小限の画面補助スクリプト
- `data/skills.json`: 技術領域データ
- `data/projects.json`: 代表プロジェクトデータ
- `docs/`: 企画、要件、設計、改善タスク管理

## テンプレート流用方針

`Spring-Tool-Development-Template` から、以下の運用基盤をポートフォリオ向けに軽量化して流用しています。

- docs階層の責務分離
- PROJECT_START_PROMPT_TEMPLATE
- TSK採番による改善タスク管理
- 作業主体分類
- 公開安全性確認

一方で、Spring Boot、Maven Wrapper、Java実装、CI整合チェックなど、ポートフォリオ静的サイトに不要な要素は流用対象外としています。

## 公開安全性

このリポジトリには、住所、電話番号、生年月日、年齢、履歴書原本、スキルシート原本、実企業名、顧客名、内部システム名、守秘義務に触れる詳細仕様を配置しません。


## 共通運用ルール正本

共通運用ルールの正本は `yamaguchiyoshishigeai-create/chatgpt-ops-rules` です。

本リポジトリでは、公開ポートフォリオ固有の掲載方針、公開安全性方針、静的サイト仕様、GitHub Pages公開前提、Works掲載方針、改善タスク管理を扱います。

共通運用ルールの参照方針は `docs/00_プロジェクト管理/05_横断運用規程/chatgpt-ops-rules中枢参照方針.md` を参照してください。
