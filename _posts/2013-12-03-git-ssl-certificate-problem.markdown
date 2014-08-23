---
layout: post
title: "gitで「SSL certificate problem: self signed certificate」と表示された時の対処法"
published: true
date: 2013-12-03 11:52
comments: true
categories:
- "雑記"
tags:
- git
keywords:
- "雑記"
- git
type: post
---
SSLの証明書に問題がある場合(このWebサイトのセキュリティ証明書には問題がありますと表示されると思います。)、「SSL certificate problem: self signed certificate」といったメッセージが表示され、リモートリポジトリからcloneできません。

対処法として以下のように入力します。

	git config --global http.sslVerify false


これで.git/configに証明書をチェックしないように設定されるので、git cloneなどした際にエラーメッセージが表示されなくなり、通常のようにできるようになります。

参考URL

- [git でオレオレ証明書のサーバを使う](http://ecpplus.net/weblog/git-%E3%81%A7%E3%82%AA%E3%83%AC%E3%82%AA%E3%83%AC%E8%A8%BC%E6%98%8E%E6%9B%B8%E3%81%AE%E3%82%B5%E3%83%BC%E3%83%90%E3%82%92%E4%BD%BF%E3%81%86/ "git でオレオレ証明書のサーバを使う")
- [GIT:リポジトリにHTTPSでアクセスしてみる](http://319ring.net/blog/archives/1164 "GIT:リポジトリにHTTPSでアクセスしてみる")


---
※この記事は WordPress に投稿した記事を変換したものです。一部不自然な表示があるかも知れません。ご了承ください。
