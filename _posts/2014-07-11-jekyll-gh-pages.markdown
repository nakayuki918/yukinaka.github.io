---
layout: post
title:  "Jekyll ＋ GitHub Pages + 独自ドメインでブログ作った"
date:   2014-07-11
type: post
---

というわけで作った。
Middleman-blogやGhostも迷ったけど、なんとなくJekyllを触ってみたかったのでJekyllにしてみた。  
デザインはテンプレートのものを少しいじっただけなので後々変えていこうと思います。

以下、手順です。

- Jekyllのインストール
- GitHub Pagesの作成
- ドメインの設定

## Jekyllのインストール

まず、自分のローカル環境にJekyllをインストールしました。  

    gem install jekyll //Jekyllのインストール
    jekyll new foobar //foobarというJekyllのテンプレートディレクトリを作成
    cd foobar //foobarディレクトリへ移動
    jekyll serve //foobarディレクトリでjekyllを始動

Jekyllのインストールについてはこんな感じです。  
`http://localhost:4000`とURLに入力すれば、ブラウザにて今動いているJekyllのプロジェクトが確認できます。

## GitHub Pagesの作成

GitHub Pagesの作成もさっくりいけます。  
メニューバーにある＋アイコンをクリックし、`New repository`を選択。  

すると、リポジトリ作成画面に移動するので、Repository nameの入力欄に`[アカウント名]＋github.io`と入力。Descriptionはお好みで。   

Initialize this repository with a READMEの項目は後から設定してもいいですが、`.gitignore`でJekyllを選択しておいてもいいかも。

## ドメインの設定

ここが一番時間かかった。ドメインに関しての知識があるとないではかなり変わってくると思う。
まず、公開する予定のディレクトリにCNAMEファイルを作成します。ファイルの中には、公開する予定のドメインを記載する。今回は、
`lab.attractr.me`というサブドメインなので、それを記述しました。   

これをGitHubにPushしてあげると、ドメインは切り替わりますが、どのサーバーを参照するかの設定が済んでないので、Web上には何も反映されません。   

次に、ドメイン側の設定をします。ちなみに私が使ってるのはムームードメインです。`attractr.me`はさくらのDNSに向けていたのですが、今回の件でムームーのDNSに切り替えました。   

下の画像が設定画面です。

<img src="/img/domain.setting.png" alt="ムームーDNSの設定" width="448" height="142" >

サブドメインを入力し、種別にCNAMEを選択、内容に作成した[アカウント名]+ github.ioを入力してあげます。元となる、`attractr.me`のドメインはさくらのレンタルサーバで運用し続けたかったので、種別でAを選択し、内容にレンタルサーバのIPアドレスを入力してあげました。   

以上で設定は終わりです。これで、`lab.attractr.me`はGitHub Pagesを参照、`attractr.me`はさくらのレンタルサーバを参照してくれるようになりました。   

あとはJekyllのプロジェクトをGitHub PagesにPushしてあげれば現在ある記事が表示されます。ちなみに`.gitignore`には`_site`が記載されているのですが、これはGitHub PagesがJekyllを動かしてくれるのでわざわざ生成する必要がないためです。自分で`.gitignore`を作る人は記載しておきましょう。


