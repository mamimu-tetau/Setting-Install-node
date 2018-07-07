# vccw

https://capitalp.jp/2017/12/16/naoki-1/
だいたいここ参照させていただいてます。


## Homebrewのインストール

### Xcodeインストール
```
$ xcode-select --install
```
### Homebrewインストール
```
$ /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```
##### インストールされているかを確認
```
$ brew doctor
Your system is ready to brew.
```
上のように Your system is ready to brew と表示されれば大丈夫。そうじゃなければ表示されているメッセージをよく読んで問題を解決しましょう。
ここで適当にあきらめて次の処理に進んでも絶対にうまく行きません。

##### Homebrewは定期的にメンテナンスが必要です。以下のコマンドは手が空いたときにやっておきましょう。

アプデ
```
$ brew update && brew upgrade
```
キャッシュを掃除
```
$ brew cleanup
```
Homebrewの動作テスト
```
$ brew doctor
```



##### vccw

```
cd [directory]
wp scaffold vccw [directory_name] --host=[host_name] --ip=192.168.33.10
ex) wp scaffold vccw vccw.test --host=vccw.test --ip=192.168.33.10
```



