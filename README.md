# gitコマンド

※ git のエイリアス設定している想定で、コマンド一部省略。

```
#ブランチ確認
git br

#ステータス確認
git st

#masterブランチ最新に更新
git pull origin master
git pull origin main

#新しくブランチきる
git co -b <ブランチ名>

#変更をステージに
git add .

#コミット
git ci -m "<メッセージ>"

#GitHubプッシュ、　※その後プルリク→コードレビュー→マージ
git push origin <ブランチ名>

↓

#マスター移動
git co master

#masterブランチ最新に更新
git pull origin master

#ブランチ削除
git br -d <ブランチ名>

#日時やコメントなどのログを確認
git log --all --graph

#リモートレポジトリをクローン
git clone クローンするURL

#リモートから変更内容をダウンロード
git fetch origin

#リモートの変更内容を取り込む
git merge origin/<ブランチ名>

#リモートからマージまで一気に取得
git pull

```
---

# [基礎]gitコマンドの復習

## ローカルリポジトリ作成 `git init`

```
gitディレクトリが作成される、(隠しフォルダなので、ls -a)
git init
```

## Git リポジトリのコピー作成(クローン) `git clone`

```
git clone <リポジトリ名>
```

## 変更をステージに追加

```
#全部
git add .

git add <ファイル名>
git add <ディレクトリ名>
```

## 変更を記録(コミット)　`git ci`

```
＃一行で簡潔にかく
git commit -m "<メッセージ>"

#vimエディタ立ち上げ、二行目に理由書く ※vimエディターiで書いて、esc→:wqで終わり
git commit -v
```


## 変更状況を確認する　 `git st`
```
#変更状況を確認する、リポジトリの状態・ステータス確認
git status
```


## 変更差分を確認する `git diff`

```
# add前の変更分
git diff
git diff <ファイル名>

#add後の変更分
git diff --staged
```


## 変更履歴を確認する、コミットしたか確認 `git log`

```
# 一行で表示
git log --oneline

#変更差分を表示
git log -p <ファイル名>

#コミット数を制限して表示
git log -n <コミット数>

#日時やコメントなどのログを確認
git log --all --graph
```


## GitHubに送信(プッシュ) `git push`

```
git push <リモート名>　<ブランチ名>
#masterブランチに
git push origin master
git push origin main

#origin(GitHub)というショートカットでURLリポジトリ登録する
#※originは、リモートリポジトリのデフォルトで付けられた名前のこと。ネット上のリポジトリを置くサーバーの登録がこのコマンド。
git remote add origin <url>
```

## ファイルの変更を取り消す `git co — `

```
#ワークツリーの変更を消したい
git checkout -- <ファイル名>
git checkout -- <ディレクトリ名>

#全変更を消したい
git checkout -- .
```

## ステージに追加した変更を取り消す `git reset`

```
#ワークツリーには、残るよ
git reset HEAD <ファイル名>
git reset HEAD <ディレクトリ名>

#ステージあるの全部消す
git reset HEAD .

#「HEAD」は、ブランチの先頭を表す名前。デフォルトはローカルリポジトリのmasterの先頭をさす。
```

## 直前のコミットをやり直す

```
#リモートにプッシュしたら、これは使えないよ
git commit --amend -m "<メッセージ>"
```

## リモートを表示する

```
#名前のみ表示
git remote

#対応するURLを表示
git remote　-v
```


## リモートから取得 `git pull`  `git fetch → git merge`

1. リモートから取得1(フェッチ→マージ)

```
#fetchした内容は、リモート/ブランチで保存される
git fetch <リモート名>
↓
#なので、ワークツリーに取り込む時は・・・　※マージ＝他人の変更内容を取り込む　マージコミット残る
git merge <リモート名>/<ブランチ名>
```

2. リモートから取得2(プル)

```
#リモートからマージまで一気に取得する　
# ※git pull <リモート名> <ブランチ名>のこと マージコミット残る
git pull
```

3. リモートから取得3(フェッチ→リベース /プルのリベース型)

```
#fetchした内容は、リモート/ブランチで保存される
git fetch <リモート名>
↓
#マージコミット残らない
git pull --rebase <リモート名> <ブランチ名>
```

## ブランチ `git br`

1. ブランチの新規追加　ブランチきる
```
#ブランチを新しく作るだけ、切り替えはしないよ
git branch <ブランチ名>
```
2. ブランチ切り替える git co
```
git checkout <ブランチ名>
```
3. ブランチの新規作成+切り替える
```
git checkout -b <ブランチ名>
```
4. ブランチの一覧表示
```
git branch

#リモートも全て表示
git branch -a
```
5. ブランチ名の変更
```
git branch -m <ブランチ名>
```
6. ブランチの削除
```
#masterにmergeしていない変更があるときは、削除しないよ　※強制削除は -D
git branch -d <ブランチ名>
```
