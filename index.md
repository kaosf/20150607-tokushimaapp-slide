% CLIでAndroid開発環境
% tokushima.app on 2015-06-07
% か [kaosfield](http://www.kaosfield.net) [Twitter](https://twitter.com/ka_)

# AndroidアプリのビルドをCLIで完結させる

# 遥か昔に自分がやってたこと

- VPSを借りる
- Android SDKをダウンロードする(`wget`などで)
- ここでおもむろにVNC Serverをインストールする
- Xをインストールする
- GUIでAndroid SDK Managerを操作して必要なものをインストール

# 利点と欠点

- 利点
    - 何をやってるのか見て分かる
    - 新しく何かを調べる必要も無い
- 欠点
    - セットアップが大変
    - `ubuntu-desktop`パッケージとか入れるの辛い
        - 必要最小限のパッケージを選べば軽いんだろうけどそれ調べるのも…

# ちょっと前に自分がやってたこと

以下のコマンドを打つ

```sh
android update sdk --no-ui --all
```

# 利点と欠点

- 利点
    - CLIだけで完結する(重要)
- 欠点
    - 全部入り状態になるので非常に時間がかかる
        - 寝る前に実行して起きたら終わってる

# 最近の自分がやっていること
<div class="incremental">

まず以下のコマンドを打つ

```sh
android list sdk --no-ui --all
```

次のような出力が得られる

```
Packages available for installation or update: 151
   1- Android SDK Tools, revision 24.3.1
   2- Android SDK Platform-tools, revision 22
   3- Android SDK Platform-tools, revision 23 rc1
   4- Android SDK Build-tools, revision 23 rc2
   5- Android SDK Build-tools, revision 22.0.1
 (中略)
 150- Android Auto API Simulators, revision 1
 151- Google Web Driver, revision 2
```
</div>

# 最近の自分がやっていること

Android SDK Managerで表示される一覧が数値によるインデックス付きで表示されている状態である

<div class="incremental">
ここで以下のコマンドを打つと指定したものだけをインストール出来る

```sh
android update sdk --no-ui --all --filter 1,2,10,100,150
```

この場合1と2と10と100と150がインストールされる
</div>

# 私が実際にインストールしているもの

```
Android SDK Tools, revision x.y.z
Android SDK Platform-tools, revision x.y.z
Android SDK Build-tools, revision x.y.z
SDK Platform Android x.y.z, API ww, revision v
Android Support Repository, revision x
Android Support Library, revision x.y.z
Google Play services, revision x.y.z
```

以上の項目に相当するものをインストールした

WebViewメインのアプリをビルドするのには困らなかった

# Ubuntuでのその他注意事項

- 以下のパッケージを必ずインストールすること
    - lib32stdc++6
    - lib32z1

<div class="incremental">
```sh
sudo apt-get install lib32stdc++6 lib32z1
```
</div>

# ここまで出来れば後は簡単

- Gradleが面倒見てくれる
- `gradlew`コマンドが実際最強

# リンク集

<ul>
<li>[このスライドのリポジトリ](https://github.com/kaosf/20150607-tokushimaapp-slide)</li>
<li>[自分のセットアップメモ](https://github.com/kaosf/ubuntu-setup/blob/master/android-setup.sh)</li>
</ul>
