# 出題1-3 まとめ


## 1.　Gitについて調べ、何をするツールで何が便利なのかなどを300ー500字程度にまとめてください

ソースコードの分散型バージョン管理システムで、元々はLinuxのソースコード管理するために作られたもの

どのファイルをいつ誰がどのように直したのか、なんのために変更したかを記録し、開発者間のソースコードの変更履歴を管理することが可能

古いファイルをもとに編集したファイルで他の作業者が更新した最新ファイルを上書きしようとする場合には警告がでるため、他人の編集内容を上書きすることを防ぐことができる

またバージョンをさかのぼって元の状態ファイルを戻すことも可能

便利な点としてブランチ機能が挙げられる
  
ブランチとは履歴の流れを分岐して記録していく機能のことで、複数の変更を同時期に実施したい場合に別々に履歴を管理することで他の作業に影響せずに作業を進められ、後に問題が発生したときの切り分けがしやすい

分岐したブランチは他のブランチと合流して一つのブランチにまとめ直すことが可能
  
- リポジトリ：ファイルのディレクトリの状態を記録する場所で変更履歴を管理したいディレクトリをリポジトリの管理下に置くとファルやディレクトリの変更履歴を記録することができる
  - リモートリポジトリ:サーバに配置して複数人で共有するリポジトリ
  - ローカルリポジトリ:作業者のマシン上に配置するリポジトリ

- コマンド
  - Pull：共有リポジトリの情報を同期
  - Commit：個人レポジトリに変更履歴を記録
  - Push：共有リポジトリに変更を共有

## 2. GitHubについて同様に調べ300ー500字程度にまとめてください

Gitリポジトリのホスティングサービスで、世界中の人がコードやデータを保存・公開できるソースコードを管理できる機能を提供している
オープンソースのコードに対してFBがもらえたり開発に参加してもらうことが可能で、ソーシャルコーディングの場としても利用されている

- 複数人での開発をより快適に進めるための機能が存在
  - プルリクエスト
    - 自分が変更したコードを取り込んでもらうようにリクエストする機能

大きなメリットとして開発効率が向上することである。GitHubでソースコードを共有することで、コードレビューやプロジェクトをすすめる上で管理がしやすいプラットフォームである

公開リポジトリは無料だが非公開リポジトリは有料

## 3. MarkDownについて同様に調べ300−500字程度にまとめてください

デジタル文書を作るためのHTMLを、テキスト上で簡略化して表記できる手軽フォーマットのことで、文章を記述するための軽量マークアップ言語の一つ

マークアップは、文章の論理的な構造や修飾に関してタグで指定する言語のことで、Markdownはより簡素に文章のレイアウトを作成できる言語である

- [日本語Markdownユーザー会](https://www.markdown.jp/syntax/)
  - 段落同士は空行で分ける
  - 箇条書きは行頭に「- 」をつける
  - 引用は行頭に「>」をつける
  - リンクしたいテキストを[]で囲み、それに続く ()にURLを書く
  - 強調したい文字を「*」で囲む

- Markdownのメリット
  - 簡易的にわかりやすいレイアウトで文章がかける
  - PDFやHTMLに変換しやすく、共有がしやすい
  - 開発エディタでも書くことができる


<br><br>


  # 出題5 作業記録

2022/02/25

## gitとは

ソースコードの分散型バージョン管理システム

## gitインストール

gitインストール参考サイト

[https://blog.cloud-acct.com/posts/u-homebrew-git-install/](https://blog.cloud-acct.com/posts/u-homebrew-git-install/)


- Homebrewとは
  - macOS用のパッケージ管理ツール


1. gitのバージョン確認

  ```
$ git --version

xcrun: error: invalid active developer path (/Library/Developer/CommandLineTools), missing xcrun at: /Library/Developer/CommandLineTools/usr/bin/xcrun
```

エラーが出ている

<br><br>
2. gitをMacにインストールする際はHomebrewを使うらしいのでバージョンを確認

```
$ brew -v

Homebrew >=2.5.0 (shallow or no git repository)
xcrun: error: invalid active developer path (/Library/Developer/CommandLineTools), missing xcrun at: /Library/Developer/CommandLineTools/usr/bin/xcrun
Homebrew/homebrew-core (no Git repository)
```
1.と同じエラーが出ている
<br><br>

仮説：コマンドを実行する際に必要な「xcrun」というものが存在していない
<br><br>


- xcrunとは

コマンドラインからデベロッパツールを見つけたり、実行する手段を提供するコマンド

参考サイト

[https://blog1.mammb.com/entry/2019/12/03/225607](https://blog1.mammb.com/entry/2019/12/03/225607)

**エラーの解消方法**

MacのOSアプデ後起こるものらしく、Xcodeをインストールし直すことで解消

```
$ xcode-select --install
```
<br><br>
3. 再度Homebrewバージョン確認

```
$ brew -v

Homebrew 3.6.8
Homebrew/homebrew-core (git revision 8b9be9832a0; last commit 2022-11-05)
```
<br><br>
4. 再度gitのバージョン確認


```
$ git --version

git version 2.37.1 (Apple Git-137.1)
```
デフォルトで入っているgitが表示される

<br><br>
5. gitインストール

今回は標準でインストールされているgitではなく、Homebrewでインストールしたgitを使用


(この時点でgitをインストールしていると勘違い)

```
$ brew info git

==> git: stable 2.38.1 (bottled), HEAD
Distributed revision control system
https://git-scm.com
Not installed
From: https://github.com/Homebrew/homebrew-core/blob/HEAD/Formula/git.rb
License: GPL-2.0-only
==> Dependencies
Required: gettext ✘, pcre2 ✘
==> Options
--HEAD
	Install HEAD version
==> Caveats
The Tcl/Tk GUIs (e.g. gitk, git-gui) are now in the `git-gui` formula.
Subversion interoperability (git-svn) is now in the `git-svn` formula.
==> Analytics
install: 349,901 (30 days), 1,083,504 (90 days), 3,806,331 (365 days)
install-on-request: 344,054 (30 days), 1,065,657 (90 days), 3,734,313 (365 days)
build-error: 42 (30 days)
```

<br><br>
6. インストールしたgitを使用するためにシェルのパスを設定


シェル確認

```
$ echo $SHELL

/bin/zsh
```
パスを設定

```
$ vi ~/.zshrc
```


<p class="warn">後続のパスの設定する箇所でzshrcではなくbash_profileを編集・確認してしまっているが、gitのバージョンはhomebrewのバージョンに無事反映できた</p>


zshrcファイルに更新した内容を確認

```
$ cat ~/.bash_profile

#HomebrewのGitを使うパス
export PATH=/usr/local/bin/git:$PATH
```

シェル再起動

```
$ exec $SHELL -l
```

インストールしたgitが反映されているか確認

```
$ git --version

git version 2.37.1 (Apple Git-137.1)
```
<br><br>

バージョン変わってない


何を考えたか：インストールし直してみよう

→コマンドの履歴を確認したらそもそもインストールしていないことが判明

今度こそインストールを実施

```
$ brew install git
```
<br><br>


gitダウンロードできたか確認

```
$ brew list

ca-certificates	git		pcre2		sqlite
gdbm		mpdecimal	python@3.10	xz
gettext		openssl@1.1	readline
```

インストールができた


zshrcファイルに設定するパスは正しくは、/opt/homebrew/binだった


[https://nullnull.dev/blog/how-to-install-latest-version-of-git-on-m1-mac/](https://nullnull.dev/blog/how-to-install-latest-version-of-git-on-m1-mac/)


```
$ cat ~/.bash_profile

#HomebrewのGitを使うパス
export PATH=/opt/homebrew/bin:$PATH
```

```
$ exec $SHELL -l
```
```
$ git --version 

git version 2.39.2
```

成功

<br><br>

# gitセットアップ

GitHubで登録したユーザ名とアドレスを設定

```
$ git config --global user.name "ユーザ名"
$ git config --global user.email アドレス
```
登録確認

```
$ cat ~/.gitconfig
```
<br><br>

# gitの使い方
  ## git init
  - リポジトリを新規作成するコマンド

デスクトップ上の「mau-j2n」フォルダにリポジトリを作成

```
$ cd ~/Desktop/mau-j2n

$ git init


hint: Using 'master' as the name for the initial branch. This default branch name
hint: is subject to change. To configure the initial branch name to use in all
hint: of your new repositories, which will suppress this warning, call:
hint: 
hint: 	git config --global init.defaultBranch <name>
hint: 
hint: Names commonly chosen instead of 'master' are 'main', 'trunk' and
hint: 'development'. The just-created branch can be renamed via this command:
hint: 
hint: 	git branch -m <name>
Initialized empty Git repository in /Users/xxxx/Desktop/mau-j2n/.git/
```
<br><br>

  ## git add

  - 作業ディレクトリ内の変更をステージングエリアに追加するコマンド

```
  $ git add README.md
```
<br><br>


  ## git commit
  - ステージングエリアの内容をローカルリポジトリに反映するコマンド

```
$ git commit

[master (root-commit) xxxxxx] initial commit
 1 file changed, 56 insertions(+)
 create mode 100644 README.md
```
  
  ## git push
  - ローカルリポジトリの内容をリモートリポジトリに反映するコマンド


1. pushする前にgitHubでレポジトリを作成


2. gitHubにレポジトリを作成後、以下コマンドでpushを実施する

```
git remote add origin https://github.com/OhPeanuts/mau-j2n.git
git branch -M main
git push -u origin main
```
<br><br>


- push実行時にユーザ名とパスワードを聞かれ入力するも以下エラーが出る

```
remote: Support for password authentication was removed on August 13, 2021.
remote: Please see https://docs.github.com/en/get-started/getting-started-with-git/about-remote-repositories#cloning-with-https-urls for information on currently recommended modes of authentication.
fatal: Authentication failed for 'https://github.com/OhPeanuts/mau-j2n.git/'
```

 仮説：認証方法が代わり、アクセストークンを作成し、使用する必要がある


**参考サイト**

[https://docs.github.com/ja/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token](https://docs.github.com/ja/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token)

[https://note.kiriukun.com/entry/20210904-github-password-authentication-was-removed
https://ios-docs.dev/20210813support-for-password/](https://note.kiriukun.com/entry/20210904-github-password-authentication-was-removed
https://ios-docs.dev/20210813support-for-password/)


[https://docs.github.com/ja/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token](https://docs.github.com/ja/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token)

-  アクセストークンとは
Personal access tokenは、GitHub API またはコマンド ラインを使用する場合に、GitHub に対する認証でパスワードの代わりに使用できるもの




## githubアカウントの作成


参考リンク
[https://codelikes.com/github-account-register/](https://codelikes.com/github-account-register/)


1. ユーザ名、メールアドレス、パスワードを設定

2. 登録したメールアドレスに届いたセキュリティコードを入力

3. 簡易的なアンケートに答える

4. 無料プランを選択

5. メールアドレスを非公開にする
メールアドレス非公開方法
https://qiita.com/OR6107/items/737bb49a5e5242980b66


## githubへのREADME.mdの公開方法


- ローカルリポジトリでREADME.mdを作成
- GitHubでリポジトリを作成（作成時に公開されるようにPublicを選択）
- Gitにてpushを実行してリモートリポジトリに反映する