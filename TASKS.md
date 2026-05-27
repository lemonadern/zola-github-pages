# Tasks

改善タスクの一覧。優先度順に並べている。

## High

- [ ] **依存 Action のバージョン更新**
  `action.yml` 内の `actions/upload-pages-artifact` が古い commit hash ピン留めになっている。v5.0.0 に更新する。

- [ ] **シェルインジェクション対策**
  `build_flags` / `check_flags` が `docker run` コマンドにそのまま展開されている。環境変数経由に変更する。

- [ ] **`include-hidden-files` 入力の追加**
  `actions/upload-pages-artifact@v5` で追加された `include-hidden-files` オプションを expose する。`.htaccess` などを含むサイトへの対応。

## Medium

- [ ] **サブモジュール対応**
  Zola テーマをサブモジュールで管理しているケースへの対応。`submodules` 入力（`false` / `true` / `recursive`）を追加するか、README でユーザー側の対応方法を案内する。
  upstream issue: getzola/github-pages#2

- [ ] **`config.toml` 不在時のエラーメッセージ改善**
  ビルド前に `config.toml` の存在チェックを入れ、分かりやすいエラーを出す。
  upstream issue: getzola/github-pages#4

- [ ] **`base_url` の上書き入力**
  PR プレビュー環境などでベース URL を差し替えられるよう `base_url` 入力を追加する。

## Low

- [ ] **Action 自体のテスト CI**
  正常系・異常系（不正バージョン文字列、`check_links` 失敗など）のテストを CI で回す。

- [ ] **Dependabot の設定**
  `.github/dependabot.yml` で `github-actions` エコシステムを監視し、依存 Action を自動更新する。

- [ ] **README の充実**
  ユースケース別サンプル（テーマあり、サブモジュールあり）やトラブルシューティングセクションを追加する。
