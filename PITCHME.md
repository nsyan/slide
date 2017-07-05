# 新卒OJT2017 Git（1,2回？）

## 前提
- 本人の現状次第なので話を聞いてから
- 必要に応じてスキップ

## なぜGitを使うのか
- バージョン（変更履歴）管理をしたい
- 複数人で同時に作業したい
- コードレビューを効率的にしたい（Gitホスティングサービスを利用）
    - マージリクエスト（GitLab）※弊社
    - プルリクエスト（GitHub, Bitbucket）

## 各バージョン管理システムのメリットとデメリット
- ファイルのコピーとリネーム（手動マンパワー）
- Subversion（集中型）
- Git（分散型）

## Gitクライアント
- [SourceTree](https://www.sourcetreeapp.com/)
- エディタやIDE
- ターミナル
- ターミナルとGUIの併用がオススメ

## 基本用語
- リポジトリ
- ブランチ
- ワークツリー
- インデックス
- クローン
- チェックアウト
- フェッチ
- プル
- プッシュ
- コミット
- マージ
- コンフリクト

## ブランチモデル
- A successful Git branching model（Git-flow）
- GitHub Flow
- GitLab Flow
- 案件によってベースのモデルや細かいルールが違う（オリジナルの場合も）

## 2種類のmerge
- Fast-Forward（mergeの代わりに早送り）
- Non Fast-Forward（早送りではない普通のmerge）
- 常に、早送りではなく普通のマージをすべきだ論

## mergeとrebase
- 怖くないmerge
- 使い方を間違えると怖いrebase
- なぜrebaseよりmergeの方が好まれるのか

## ケーススタディ
まずはターミナルで

- ベーシックなフロー: clone, branch, checkout, status, add, commit, fetch, pull, push
- マージとコンフリクトの解消: merge
- タグを付ける: tag
- 空コミットでコメント: commit
- ローカルの変更を無視: update-index
- ファイルを管理対象から外す: rm
- ローカルの変更を一時的に保存: stash
- ログを確認: log
- ヘッドの履歴を確認: reflog
- ブランチ間の差分を見る: diff
- ワークツリー・インデックスを元に戻す: reset
- 指定コミットを打ち消す: revert
- 特定のコミットのみ適用: cherry-pick

## その他
- コミットメッセージ
- コミット粒度
- コードレビュー

## 課題？
- これからの各課題において、Gitでバージョン管理をしてみよう
- 新卒用GitLabのリポジトリ？
    - PrivateのProject追加

## 追加
- GitHubのアカウントがなければ作っておく
- ブランチを切り替えるとローカルファイルが丸ごと変わるという現実
    - ファイルの状態による（add, commitの状態の話)
- Gitこわくない
- 何かあった時は無理して自分で解決しようとせず相談（悪化する可能性が高い）


---


## 参考サイト
- [サルでもわかるGit入門 〜バージョン管理を使いこなそう〜 \| どこでもプロジェクト管理バックログ](http://www.backlog.jp/git-guide/)
- [Git チュートリアルとトレーニング\| Atlassian](https://www.atlassian.com/ja/git/)
- [こわくない Git](https://www.slideshare.net/kotas/git-15276118)
- [gitのmerge \-\-no\-ff のススメ \- Qiita](http://qiita.com/nog/items/c79469afbf3e632f10a1)
- [【初心者向け】Gitってなに？①まず流れを理解する（コードなし） \- Qiita](http://qiita.com/nutsinshell/items/96cb83aecf9d09a7a8bc)
- [Git 基本の用語集 \- Qiita](http://qiita.com/toshi_um/items/72c9d929a600323b2e77)


## Subversion（SVN）との違い
- [SVNを捨ててGitを使うべき5つの理由 \- Qiita](http://qiita.com/YusukeHosonuma/items/14c59f3878d640a401a1)
- [Subversion 対 Git：どちらを使うべきなのか？いろいろな観点から比較してみた \| tracpath:Works](http://tracpath.com/works/development/subversion_vs_git/)
