## vccw
##### vccw

公式サイトからインストーラーをダウンロード
https://nodejs.org/en/
バージョン管理とかする場合はゴニョゴニョしてください。
node.jsをインストールをするとnpmコマンドが使えるようになります。

```
cd [directory]
wp scaffold vccw [directory_name] --host=[host_name] --ip=192.168.33.10
ex) wp scaffold vccw vccw.test --host=vccw.test --ip=192.168.33.10
```

## Homebrew
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
