---
layout: post
title:  "WordPressのブログをJekyllに移行してGitHub Pagesで運用することにした"
date:   2014-08-24
type: post
---

[直前の記事](/jekyll-gh-pages/)でブログを作ったけど、あまりブログの数が乱立するのもよくないと思い、WordPressで運用していたブログをGitHub Pagesに移した。

元々、GitHub Pagesにあったブログは、大して記事もなかったので、ドメインごと削除しました。本来それは、Tips的な備忘録として扱う予定だったのだけれど、最近は[Qiita](http://qiita.com/)に残していくのが主流なのかなと思ったので、今後はQiitaに残していこうと思う。

簡単にやったことを以下にまとめます。

- WordPressの記事の出力と取り込み
- ドメイン(DNS)とかの設定

## WordPressの記事の出力と取り込み

言わずもがな、地味にこれがめんどうだった。

[@ayumiko](https://twitter.com/ayumiko)さんの[WordPressからmiddlemanに移行してGithub Pagesで運用する方法](http://camuro.org/blog/2013/09/renewal.html)を参考にさせていただきました。

僕はmiddlemanではなく、Jekyllを使用しているけど、やることは大体一緒。手順としては以下のとおり。

1. WordPressからxmlをエクスポート
2. [WpXml2Md](https://github.com/komasaru/WpXml2Md)でxmlをコンバート
3. コンバートしたMarkdownファイルを地道に修正(遠い目)

3をやったのは、やはり体裁に合わない箇所が多かったから。

記事数が少なかったので僕はやったけど、WpXml2Mdで「※この記事は WordPress に投稿した記事を変換したものです。一部不自然な表示があるかも知れません。ご了承ください。また、記事タイトル先頭の * は WordPress から移行した記事である印です。」という文章を自動でいれてくれるので、めんどうだと思った人は最悪やらなくてもいいかも。

## トップレベルドメインでDNSの変更

これが前回の記事とは違うところで、サブドメインで使用するのとやることが変わってくる。

サブドメインだとDNSプロバイダでCNAMEレコード設定して、CNAMEファイルを設置するのだけれど、トップレベルドメインだとAレコードを設定する。

DNSプロバイダで`192.30.252.153`,`192.30.252.154`2つのIPアドレスを設定する。

反映が済んでいるかを以下のように確認する。

ターミナルで

	dig example.com +nostats +nocomments +nocmd

を入力すれば、

	<<>> DiG 9.8.3-P1 <<>> example.com +nostats +nocomments +nocmd
	;; global options: +cmd
	;example.com.			IN	A
	example.com.		3600	IN	A	192.30.252.153
	example.com.		3600	IN	A	192.30.252.154

といった感じで表示されると思う。あとは、CNAMEファイルを作成して終わり。

クローンしてあるリポジトリ内にて、

	echo example.com(ドメイン名) > CNAME

と入力すればCNAMEが作成される。

このあたりは、GitHub Helpの[Tips for configuring an A record with your DNS provider](https://help.github.com/articles/tips-for-configuring-an-a-record-with-your-dns-provider)を見るのがいい。

以上です。

デザインやら何やらは徐々に直していこうと思います。

## 追記(2014/08/25)

どうやらAレコードの設定だけだと、GitHub PagesのCDNが効かないらしく、
「[ムームードメイン+GitHub Pagesで独自ドメインを使う方法](http://hamasyou.com/blog/2014/03/05/github-pages-custom-domain/)」を読んで、Apex Aliasの設定をしました。詳細はこの記事を読めば分かると思うので省略します。

前述のAレコードでの設定を行っている人は、Apex Aliasの設定終了後、DNSレコードでの設定で無効にするなり削除して下さい。

ちなみにターミナルにて以下のように叩けばステータスコードが200で返ってくるか確認できます。

	curl -I http://code-plus.jp //ドメイン名
	HTTP/1.1 200 OK
	Server: GitHub.com
	//以下省略

設定できていないと、`HTTP/1.1 200 OK`の箇所が`302 Found`で返ってくることがあります。