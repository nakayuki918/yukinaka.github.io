---
layout: post
title: "data URI Scheme(base64エンコード)ならSass+Compassがおすすめ"
published: true
date: 2013-04-01 08:11
comments: true
categories:
- CSS・CSS3
tags:
- CSS
- Sass
keywords:
- CSS・CSS3
- CSS
- Sass
type: post
---
通常、data URI Schemeを作成しようとすると、「画像を作成→base64エンコード→CSSに記述」という流れになり、結構手間がかかります。またCSSには元の画像名などが記載されないため、元ファイルが何なのか分かりづらく、管理もしづらくなりがちです。
しかし、Sass+Compassを使用することで、簡単にdata URI Schemeを作成し、管理もしやすくすることができるようになります。

参考:[CompassでデータURI スキーム](http://blog.webcreativepark.net/2012/06/17-120506.html "CompassでデータURI スキーム")

## scssファイルへの記述方法

以下のように、CSSでは「url」となる部分を「inline-image」に変更するだけです。
(※クォーテーションも必要です。)

	//サンプルアイコン
	.icn-sample {
		background-image: inline-image("img/sample.png");
	}


何故、管理しやすくなるかというと、コメントが残せる(CSSには反映されない)ことに加えて、元の画像ファイル名が分かるからです。通常のCSSでは、エンコード後のものを記述するので、コメントでも残しておくか、クラス名を明確化していない限り、元のファイルが何だか分かりません。

またエンコード作業が「inline-image」の記述のみで済むというのが何よりの魅力だと思います。

## 終わりに
data URI Schemeを使用するとHTTPリクエストを減らすことができるので、使い方次第で高速化に繋げることができます。今回のこの方法は非常に便利ですので、data URI Schemeを使用するという際には是非この方法を試して見てください。

---
※この記事は WordPress に投稿した記事を変換したものです。一部不自然な表示があるかも知れません。ご了承ください。
