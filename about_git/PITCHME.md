# Git基本のキ
2017新卒OJT

---

## まず伝えたいこと

+++

- ローカルファイルが丸ごと変わるという現実
    - ファイルの状態による（`add`, `commit`, `push`)
- Git`こわくない`
- 何かあった時は、無理して自分で解決しようとせずに`相談`（悪化する可能性が高い）

---

## なぜGitを使うのか

+++

### バージョン（変更履歴）管理をしたい
いつ、何に、誰が、何をしたのか

- ファイル履歴とコミットメッセージ

+++

### 複数人で同時に作業したい

- 場合によっては同じファイルも

+++

### コードレビューを効率的にしたい
- Gitホスティングサービスを利用
- マージリクエスト（`GitLab`）※弊社
- プルリクエスト（GitHub, Bitbucket）  

※[GitHub](https://github.com/)のアカウントがなければ作成

---

## 各バージョン管理システムのメリットとデメリット

+++

### ファイルのコピーとリネーム<br>（手動マンパワー）

+++

### Subversion<br>（集中型）
リポジトリが一つ（リモート）

+++

### Git<br>（分散型）
リポジトリが複数（リモート、ローカル）

+++

### リポジトリとは
ファイルやディレクトリの状態を管理する場所（追加、変更、削除）

- リモートリポジトリ：サーバに配置して複数人で共有
- ローカルリポジトリ：各々がそれぞれのPCで使う

---

## 基本用語

+++

- ブランチ  
履歴管理を枝分かれさせたもの。複数の履歴を`並列に管理`できる。
- クローン  
リモートリポジトリをコピーしてローカルリポジトリを作成（`clone`）
- チェックアウト  
ブランチやコミットを切り替える（`checkout`）

+++

- マージ
異なるブランチの変更を反映させる（`merge`）  
※お互いの変更履歴が`残る`
- リベース  
異なるブランチの変更を反映させる（`rebase`）  
※変更履歴が片方に集約される（片方は`消える`）
- コンフリクト（衝突）  
マージ対象のファイルで同じ部分が変更されており、自動マージができない状態。

+++

- フェッチ  
リモートリポジトリの最新の履歴の取得だけを行う（`fetch`）  
※ファイルの`更新はしない`
- プル（フェッチ＋マージ）  
リモートリポジトリの変更をローカルリポジトリに反映（`pull`）  
※ファイルが`更新（マージ）される`
- ワークツリー（ワーキングツリー）  
実際に作業しているファイルがある場所

+++

- インデックス  
コミットしたいファイルを登録する場所（`add`）
- コミット  
インデックスに登録してある変更対象をローカルリポジトリに反映（`commit`）
- プッシュ  
ローカルリポジトリの変更をリモートリポジトリに反映（`push`）

---

## Gitのメリット

+++

### ローカルでブランチが気軽に切れる
- 自分専用のブランチが持てる
- ブランチ間のマージも容易

+++

### ローカルコミットができる
- 途中段階でもコミットできる
- 他の開発者に影響を与えない

+++

### ネットワークがなくても作業可能
- ローカルブランチ

---

## Gitクライアント

+++

- <a target="_blank" href="https://www.sourcetreeapp.com/">SourceTree</a>
- エディタやIDE
- ターミナル、<a target="_blank" href="https://www.iterm2.com/">iTerm2</a>
- ターミナルとGUIツールの併用がオススメ

---

## ブランチモデル

+++

### <a target="_blank" href="http://nvie.com/posts/a-successful-git-branching-model/">A successful Git branching model（Git-flow）</a>
- プロダクトを厳格にリリースする＝冗長すぎる場合も
- マージの回数が増えがち＝取り込み忘れ、コンフリクト、確認、解消ミスの手間とリスクが増える

+++

### <a target="_blank" href="http://scottchacon.com/2011/08/31/github-flow.html">GitHub Flow</a>
- masterと作業用のブランチの2種類のみ
- masterは常にデプロイ可能という前提

+++

### <a target="_blank" href="https://about.gitlab.com/2014/09/29/gitlab-flow/">GitLab Flow</a>
- masterは作業用、他にリリース準備用、デプロイ用のブランチがある

+++

- 案件によってベースのモデルや細かいルールが違う
    - オリジナルの場合も
- リリースをどう捉えるか

---

## 2種類のマージ

+++

### Fast-Forward<br>（マージの代わりに早送り）

++

### Non Fast-Forward<br>（早送りではない普通のマージ）

+++

### 常に早送りではなく普通のマージをすべき
- <a target="_blank" href="https://www.slideshare.net/kotas/git-15276118/40">こわくない Git</a>

```
git config --global --add merge.ff false
git config --global --add pull.ff only
```

+++

### Gitの設定ファイル
- `gitconfig`  
Gitの様々な設定
    - `/Users/hoge/.gitconfig`
- `gitignore`  
意図的に追跡対象から外したい（無視したい）ファイルを設定
    - `/Users/hoge/.gitignore_global`: グローバル
    - `/Users/hoge/work/fuga/.gitignore`: ローカル

---

## マージとリベース

+++

- こわくないマージ
- 使い方を間違えると怖いリベース
- なぜリベースではなくマージなのか
- <a target="_blank" href="https://www.slideshare.net/kotas/git-15276118/100">こわくない Git</a>

---

## ケーススタディ

+++

- ベーシックなフロー  
`clone, branch, checkout, status, add, commit, push, fetch, pull`

+++

```
git clone
git checkout -b hoge  // ブランチを作成してチェックアウト
git add .  // .gitignoreで指定されたファイル以外のすべてのファイルをステージ
git commit
git push
```

+++

### ターミナルのショートカット
- tab: 補完（コマンド、ブランチ名、--オプション）
- ↑↓: コマンド履歴
- cmd+k: ターミナルの履歴削除
- その他たくさん
- ターミナルに限らず効率化

+++

- マージとコンフリクトの解消: `merge`
    - \>\>\>, <<< で検索
    - コンパイル後のminifyファイルでありがち<br>（js, css）

+++

`自分以外の人と並行作業しているブランチ`でコンフリクトが起きた時は
自分の判断だけで解消せず、必ずチーム（担当者）とすりあわせる。

+++

- タグを付ける: `tag`
    - コミットを参照しやすくするために、わかりやすい名前を付ける
    - リリース時

+++

```
git tag tag1
git push origin --tags
```

+++

- 空コミットでコメント: `commit`
    - ファイルの変更なくコミットが可能
    - ブランチに何かコメントを残したい時など

+++

```
git commit --allow-empty -m "大人の事情でペンディング"
```

+++

- 直前のコミット（メッセージ）を修正
    - メッセージを間違えた、typoした
    - addや修正が抜けてた

+++

```
git commit
抜けてたことの対応
git commit --amend  // 前のコミットに上書き
```

+++

- ローカルの変更を無視: `update-index`
    - リモートにpushしたくないが、ローカルで変更したい場合
    - 解除しないと無視し続けるので注意

+++

```
git update-index --assume-unchanged Gruntfile.js  // 無視
git update-index --no-assume-unchanged Gruntfile.js  // 無視解除
```

+++

- ファイルを管理対象から外す: `rm`
    - Gitで管理する必要がないファイル
    - node_modules, .sass-cache など
    - 基本的には.gitignoreされているはず

+++

```
git rm index.html  // ファイルも消える
git rm --cached index.html  // ローカルにファイルは残る
// 監理対象から外したというコミットをpush
```

+++

- ローカルの変更を一時的に退避: `stash`
    - 作業途中にブランチを変更したい
    - 急に差し込みが入った
    - 今の内容を保存しつつ、別の変更をしたい

+++

```
error: Your local changes to the following files would be overwritten by checkout:
Please commit your changes or stash them before you switch branches.
Aborting
```

+++

```
git stash save 'comment'  // 退避 saveは省略可
git stash list  // 一覧表示
git stash pop  // 復元（stashは消える）オプションで残せる
git stash drop  // 退避を削除
git stash clear  // 退避を全削除
```

+++

- ログを確認: `log`

+++

```
git log --oneline --graph  // そこそこ見やすく
```

+++

- HEADの履歴を確認: `reflog`
    - コミット履歴の一覧
    - コミットメッセージの1行目（後述）

+++

```
git reflog
git reset --hard HEAD@{1}  // 1つ前のHEADに戻す
```

+++

- 差分を見る: `diff`
    - ブランチ間
    - コミット間
    - ファイル間

+++

```
git diff --cached  // HEADとインデックスの差分（add済
git diff HEAD  // HEADとワーキングツリーの差分（add前
git diff コミットID コミットID  // コミット間
git diff ブランチA ブランチB  // ブランチ間
git diff -w  // 改行コードや空白を無視
```

+++

- ワークツリーやインデックスを元に戻す（取り消す）: `reset`
    - \-\-hard：全て戻す（ファイルも）
    - \-\-mixed（オプションなし）：commitとaddの取り消し
    - \-\-soft：commitのみ取り消し

+++

```
git reset --hard  // コミット前の変更をすべて取り消す
git reset --soft HEAD^  // 直前のコミットのみ取り消す（コミット前に戻す）
git reset  // addを取り消す
git reset --hard HEAD^  // 直前のコミットを全て取り消す
```

+++

- ローカルな変更を元に戻す
- 公開済みの変更の取り消しをしようとしてはならない→`revert`

+++

- 指定コミットを打ち消す: `revert`
    - 変更を元に戻す新しいコミットを生成
    - 過去に公開したコミットを安全に打ち消す

+++

```
git revert HEAD  // 1つ前のコミットを打ち消し
git revert コミットID
```

+++

- 特定のコミットを抜き取る: `cherry-pick`
    - 別ブランチのコミットを現在のブランチにも追加する

+++

```
git cherry-pick コミットID
```

---

## その他

+++

### コミットメッセージ
```
1行目：変更内容の要約（タイトル、概要）
2行目：空行
3行目以降：変更した理由（内容、詳細）なぜ
```
※案件によってはルールがある

+++

### コミット粒度
- 細かすぎても大雑把すぎてもダメ
- 履歴の確認やロールバック（巻き戻し）
- コミットのピックアップ: `cherry-pick`

+++

### コードレビュー
- GitLabのマージリクエストを利用

---

## 課題

+++

これからの各ジャンルの課題において、Gitで色々やってみましょう。
