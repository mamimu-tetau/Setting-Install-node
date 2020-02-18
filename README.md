# node + Gulp

## Toc
- [Homebrew](#homebrew)
  - [Xcodeインストール](#xcodeインストール)
  - [Homebrewインストール](#homebrewインストール)

- [Homebrewメンテナンス](#homebrewは定期的にメンテナンスが必要です以下のコマンドは手が空いたときにやっておきましょう)

- [主要なコマンドのインストール](#主要なコマンドのインストール)
  - [gitインストール](#gitインストール)
  - [PHPインストール](#PHPインストール)
  - [MySQLのインストール](#MySQLのインストール)

- [Gitの設定](#gitの設定)

- [Nodeのインストール](#nodeのインストール)
  - [nodebrewをインストール](#nodebrewをインストール)
  - [nodebrewで使いたいバージョン選択](#nodebrewで使いたいバージョン選択)

<br /><br /><br /><br />

## Homebrew
以下はターミナルでのコマンドです。
<br /><br /><br />

### Xcodeインストール
```
$ xcode-select --install
```
### Homebrewインストール
```
$ /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```
途中でパスワードを聞かれたらMacのユーザーパスワードを。

##### インストールされているかを確認
```
$ brew doctor
```
 `Your system is ready to brew` と表示されれば大丈夫。そうじゃなければ表示されているメッセージをよく読んで問題を解決しましょう。<br />
ここで適当にあきらめて次の処理に進んでも絶対にうまく行きません。<br />
nodeとかパッケージ版でインストールしているとガンガンエラー出ますw
<br /><br /><br /><br />




##### Homebrewは定期的にメンテナンスが必要です。以下のコマンドは手が空いたときにやっておきましょう。

##### アプデ
```
$ brew update && brew upgrade
```
##### キャッシュを掃除
```
$ brew cleanup
```
##### Homebrewの動作テスト
```
$ brew doctor
```
<br /><br /><br /><br />




## 主要なコマンドのインストール

### gitインストール
```
$ brew install git curl
```
### PHPインストール
以下のコマンドで
```
$ php -v
```
`PHP 7.3.11 (cli) (built: Dec 13 2019 19:21:21) ( NTS )`など既にインストールされているphpで問題なければphpインストールは飛ばしてください。<br />
使いたいPHPバージョンをインストールします。必要に応じて切り替える場合は
[brewでphpバージョン切り替え](https://qiita.com/gyarasu/items/0ffd0fb5761b9d164d39)
```
$ brew install php73
```

### MySQLのインストール
Local by flywheelなどでDBを利用する場合は不要です。インストールは飛ばしてください。
```
$ brew install mysql
```
次にインストールした MySQL がパソコンの再起動後に自動的に起動するようにします。
```
$ brew services start mysql
```
<br /><br /><br /><br />

## Gitの設定
Gitにユーザー名とメールアドレスを設定します。今回は無難にGitHubのユーザー名とメールアドレスを設定しましょう。  
GitHubにサインアップしていない場合はサインアップしてください。  
サインアップしたらGitHubのユーザー名を以下のように設定します。 username の部分をみなさんのGitHubのユーザー名と置き換えてください。  
```
$ git config --global user.name "username"
```
```
$ git config --global user.email "xxx@xxx.com"
```
<br /><br /><br /><br />





## Nodeのインストール

~~gulpでgulp-sassを使う場合バージョン8.xが求められたのでnodeのバージョンを切り替えられるnodebrewでのインストールを推しますw~~<br />
Gulp v4リリースで特にバージョン切り替えは必要ないのですが管理用に入れておいたほうが良いです。

#### nodeがすでにインストールされていないか確認。
```
$ brew ls 
```
表示された中にnodeあるならアンインストールが必要です。 
```
$ brew uninstall --force node
```
nodeがすでに他の方法でインストールされていないか確認。

```
$ node -v 
```
バージョンが出てくればパッケージ版のnodeをすでにインストールしている模様なのでアンインストール。。。苦戦してくだしあ）  
<br /><br />


#### nodebrewをインストール
```
$ brew install nodebrew
```
```
$ nodebrew
nodebrew 1.0.1
...
```
nodebrewで使えるコマンドが出てくればOK
<br /><br />



#### nodebrewで安定版バージョンのnodeをインストール

```
$ nodebrew install-binary stable
```
stableは現行の安定版ってことなのでバージョン指定の場合はv12.16.0とか入れてください。
参考：https://nodejs.org/en/blog/


```
Fetching: https://nodejs.org/dist/v12.16.0/node-v12.16.0-darwin-x64.tar.gz
Warning: Failed to create the file                                                        
Warning: /Users/hacca/.nodebrew/src/v12.16.0/node-v12.16.0-darwin-x64.tar.gz: 
Warning: No such file or directory
                                                                                       0.0%
curl: (23) Failed writing body (0 != 1019)
download failed: https://nodejs.org/dist/v12.16.0/node-v12.16.0-darwin-x64.tar.gz
```
ディレクトリがねぇぞバカヤローって場合は。。

```
$ mkdir -p ~/.nodebrew/src
```

#### nodebrewのセットアップ
```
$ nodebrew setup
========================================
Export a path to nodebrew:

export PATH=$HOME/.nodebrew/current/bin:$PATH
========================================
```


#### 環境変数を追加
```.bash_profile```に```export PATH=$HOME/.nodebrew/current/bin:$PATH```のPATHを追加（1行目とかに）<br /><br />

.bash_profileが存在しない場合があるので
```
$ touch ~/.bash_profile
```
ほんで編集
```
$ vi ~/.bash_profile
```
```.bash_profile```に```export PATH=$HOME/.nodebrew/current/bin:$PATH```のPATHを追加（1行目とかに）<br />
viコマンドが初めての場合！！！ってなるかも。まずは基本的なviエディタの使い方は調べてね。<br /><br />
私の場合```i```キー押して通常のモードにして操作します。で```esc```キー押してコマンドモードに戻って```:wq```で保存です。やばい時は```esc```からの```:q!```で何もせず戻るw 
<br /><br />

有効化
```
$ source ~/.bash_profile
```

#### nodeのバージョン選択
```
$ nodebrew ls

current: none
```
インストールされているnodeのバージョンを確認。`v12.16.0 current: none`とかが出る

```
$ nodebrew use v12.16.0　//バージョンを指定
$ node -v
```
確認。`v12.16.0`バージョンが出ればOK。

#### nodeのバージョン変更とかはこちらを
https://qiita.com/oreo3@github/items/622fd6a09d5c1593fee4

<br /><br /><br /><br />










# ここから先はWP-CLIとかvccwのインストール。Gulp使うだけならここまで。

## Rubyのインストール
```
$ brew install ruby
```
<br /><br /><br /><br />

## WP-CLIのインストール
```
$ cd
$ curl https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli-nightly.phar -o wp
$ chmod 755 wp
$ mv wp /usr/local/bin/
```
最後に wp --info で動作確認しましょう。以下のような出力に（だいたい）なっていればオッケーです。
```
$ wp --info
PHP binary:	/usr/local/Cellar/php72/7.2.0_11/bin/php
PHP version:	7.2.0
php.ini used:	/usr/local/etc/php/7.2/php.ini
WP-CLI root dir:	phar://wp-cli.phar
WP-CLI vendor dir:	phar://wp-cli.phar/vendor
WP_CLI phar path:	/Users/miya
WP-CLI packages dir:	/Users/miya/.wp-cli/packages/
WP-CLI global config:	
WP-CLI project config:	
WP-CLI version:	1.5.0-alpha-d71d228
```
この時点でうまく行っていなければ一番最初からやり直してください。
<br /><br /><br /><br />



## WP-CLIのコマンド補完を有効化する
以下のコマンドで必要なスクリプトをインストールします。
```
$ curl -L https://raw.githubusercontent.com/wp-cli/wp-cli/master/utils/wp-completion.bash -o ~/.wp-completion.bash
```
次に``` ~/.bash_profile ```に設定を記述します。
```
source ~/.wp-completion.bash
```
ターミナルを開き直すか```source ~/.bash_profile```コマンドを実行して設定を反映させてください  
<br /><br /><br /><br />




## 初心者がコマンドと付き合うときに最低限覚えておくべきこと
### sudo は安易に実行しない
```sudo```は root 権限と呼ばれるとても大きな権限でコマンドを実行するために使用します。  
この記事で```sudo```を一度も実行していないことからも分かる通り、ローカル環境で```sudo```を使用することはめったにありません。  
一度これで実行してしまうと次回以降つねに```sudo```をしてしまわないといけなくなりますし、権限が大きいためにシステムのトラブルを招きやすいだけでなく悪意があるコードをとても大きな権限で実行してしまうリスクもあります。  
```sudo```は使用しないでください。また安易に```sudo```を書いてあるブログ等は見る価値がありません。
<br /><br /><br /><br />



## 仮想環境のインストール

### Vagrantインストール
[Vagrant](https://www.vagrantup.com/downloads.html?utm_source=capitalp&utm_campaign=SponsorUs&utm_medium=voluntary_link)


### Virtualboxインストール
[Virtualbox](http://www.oracle.com/technetwork/server-storage/virtualbox/downloads/index.html?ssSourceSiteId=otnjp&utm_source=capitalp&utm_campaign=SponsorUs&utm_medium=voluntary_link)

#### Vagrantプラグインインストール
```
$ vagrant plugin install vagrant-hostsupdater
```
```
$ curl https://raw.github.com/brbsix/vagrant-bash-completion/master/vagrant-bash-completion/etc/bash_completion.d/vagrant -o vagrant
$ mv vagrant `brew --prefix`/etc/bash_completion.d/
```
最後に以下のコードを```~/.bash_profile```にコピペして```、source ~/.bash_profile```するかターミナルを再起動してください。
```
if [ -f `brew --prefix`/etc/bash_completion.d/vagrant ]; then
    source `brew --prefix`/etc/bash_completion.d/vagrant
fi
```
<br /><br /><br /><br />




### Vagrantの使い方

```vagrant up``` – 起動  
```vagrant halt``` –  停止  
```vagrant destroy``` – 廃棄  
```vagrant provision``` – 再構築  
```vagrant global-status``` – 全マシンのステータスを確認  
<br /><br /><br /><br />




## VCCW
VVVとの最大の違いはWordPress本体の開発を想定していないことです。  
VCCWはWordPress本体の開発に必要な様々なパッケージ類をダウンロードしない一方で、ウェブサイトやテーマ、プラグインの開発に特化しているため、VVVに比べて起動が早く使用するディスク容量も比較的小さくなっています。  
YAMLファイルやシェルスクリプト、Ansibleによるカスタマイズも可能で、初回のBoxのダウンロードを除くと最小構成で2分ほどで起動します。  
<br /><br /><br /><br />



### VCCWの使用方法
VCCW環境を簡単につくるための WP-CLI 環境が用意されています。まずそれをインストールしましょう。
```
$ wp package install vccw/scaffold-vccw:@stable
```
もしかしたら以下のようにメモリが足らないというエラーがでるかもしれません。
```
PHP Fatal error:  Allowed memory size of 268435456 bytes exhausted
```
その場合は以下のようにして一時的にPHPのメモリーリミットを無制限にして実行します。
```
php -d memory_limit=-1 /usr/local/bin/wp package install vccw/scaffold-vccw:@stable
```
  
次にVCCWの設定ファイルをつくります。  
以下の内容を ~/.vccw/config.yml に記述してください。  
```
memory: 1024
cpus: 2
linked_clone: true
```
  
```.vccw```がなかったら作ります
```
mkdir -p ~/.vccw
```
  
```config.yml```がなかったら作ります
```
touch ~/.vccw/config.yml
```
<br /><br /><br /><br />




### VCCW起動
ここからが新しく環境を作る時に毎回行うやつです。
今回はデスクトップに作ります
```
$ cd ~/Desktop
$ wp scaffold vccw vccw.test --host=vccw.test --ip=192.168.33.10 --lang=ja
```
```wp scaffold vccw [ディレクトリ名] --host=[ドメイン] --ip=192.168.33.10 --lang=ja```
ホスト名 vccw.test の部分と IP アドレス 192.168.33.10 はお好みでどうぞ。  
  
次にマシンを起動します。最初はBoxと呼ばれるベースになるハードディスクイメージをダウンロードしますので20分ほど時間がかかるかもしれません。
```
$ cd vccw.test
$ vagrant up
```
終わったらブラウザでサイトにアクセスしてみましょう。
[http://vccw.test/](http://vccw.test/)

以下のコマンドを実行することで開くこともできます。
```
$ wp browse
```

管理画面なら以下のような感じ。
```
$ wp browse --wp-admin
```
<br /><br /><br /><br />




## VCCWにphpMyAdminを入れる
下記よりダウンロードしたzipを解答し、フォルダ名を「phpmyadmin」と変更します。変更した「phpmyadmin」フォルダを「wordpress」下に設置します。
[phpMyadmin](https://www.phpmyadmin.net/downloads/)

```
vagrant up
vagrant ssh(必要？)
```
vagrantを起動して「http://192.168.33.10/phpmyadmin」とアドレスバーに入力します。「192.168.33.10」はVCCWを導入する準備として、hostsに設定したものになります。  
初期設定ではユーザー名は「root」、パスワードは「wordpress」となっています。
<br /><br /><br /><br />


## VCCWのDBまるごとgitとかで共有する

流れ的には

- DBバックアップ
- VM止める(```vagrant halt```もしくは```vagrant destroy```で共有内容確認)
- ```/wordpress/gitignore```の共有内容確認
- git commit（リポジトリ作ってコミット)
- git push（リモートリポジトリにアップ)
- git clone
- vagrant up（provision-post.shでDBインポート）


### DBバックアップ 
```
$ vagrant up
```
マシンに入る
```
$ vagrant ssh
```
dbをエクスポート
```
$ wp db export /vagrant/wordpress.sql
```
以上で、ホストマシンから見ると Vagrantfile と同じディレクトリに wordpress.sql というファイルができてるはず。  
<br /><br />

### vagrant upでsqlを自動インポートさせる。
VCCWでは、provision-post.shというシェルスクリプトを用意しておくと、プロビジョニングの最後にそのシェルスクリプトが発火するようになっています。  
そこで、provision-post.shというファイルに下記を記述し、Vagrantfile と同じディレクトリに設置してください。  
これでまるごとgitにシェアしてダウンロードすれば環境共有できます。  
```
#!/usr/bin/env bash

set -ex

if [ -e /vagrant/wordpress.sql ]; then
  sudo -u vagrant -- wp db import /vagrant/wordpress.sql
fi

```
<br /><br />

### ```/wordpress/gitignore```の共有内容確認

アップした画像とかもろもろ共有したい場合は
```/wordpress/gitignore```の
```
wp-content/upload/
```
とか削除してからgit commitしてください。
<br /><br />

dbの変更をシェアする場合は毎回エクスポートして別環境でインポート(vagrant up)してください。
```
$ vagrant ssh
$ wp db export /vagrant/wordpress.sql
```

インポートは
```
$ vagrant up
```
もしくは
```
$ vagrant ssh
$ wp db import /vagrant/wordpress.sql
```
もしくは
```
$ vagrant provison
```
<br /><br /><br /><br />




## うまく動かない！！
```
$ vagrant global-status
```
で他のマシンが無いか確認して見てください。  
もしすでに起動中のゲストマシンがあれば、同じホスト名、同じIPアドレスでは起動できません。  
さらに、```/etc/hosts```も確認してください。 Vagrant のプラグイン hosts-updater を使用するとホストの情報を自動的に書き込んでくれますが、この情報がうまく削除されずに残っていることがあります。
<br /><br /><br /><br />


## VCCWとgulpとbrowsersync
hostsにipv6用のアドレスも追加しないと激重  
viエディタの使い方は調べてね
```
vi /private/etc/hosts
```
下記を追記
```
::ffff:c0a8:210a ドメイン
```
192.168.33.10をipv6に変換すると→::ffff:c0a8:210aな感じで変換して書いておく  
[ipアドレス変換サイト](https://awebanalysis.com/ja/ipv4-to-ipv6-convert/)
<br /><br /><br /><br />



# TroubleShoot

## vagrant upでbox already exist
VMをdestroyしないままディレクトリ削除したりするとなる？

```
vagrant global-status
```
で起動中や存在するBOXを確認する。

```
vagrant destory ボックス名
```
で削除。下記のエラーが出るかも。
```
A virtualBox machine with the name .... already exist
```
まずは

```
vagrant global-status --prune
```
でキャッシュを削除

それでダメなら/User/あなた/VirtualBox VMs/該当ディレクトリ削除<br><br><br>


## Snapshotファイルの肥大化
ずっとVM使っていくとSnapshotファイルが肥大化してくるようです。.vmdkとかいうファイル。
なのでたまにDBのエクスポートしてsite.ymlのバージョン合わしたりしてDestroyすると軽くなる
