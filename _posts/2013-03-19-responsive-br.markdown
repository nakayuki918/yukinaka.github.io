---
layout: post
title: "レスポンシブWebデザインでの改行位置の変更方法"
published: true
date: 2013-03-19 09:29
comments: true
categories:
- CSS・CSS3
tags:
- CSS
- RWD
- "テクニック"
keywords:
- CSS・CSS3
- CSS
- RWD
- "テクニック"
type: post
---
HTMLの文章中にて&lt;br&gt;で改行位置を指定していると、Media Query等でスタイルが切り替わった際に改行が残ってしまい、デバイスによっては見た目上いいとは言いがたい状態になってしまいます。

CSSを使用しての2つの対策方法を紹介します。

参考サイト:[“Responsive Line Breaks,” an article by Dan Mall](http://danielmall.com/articles/responsive-line-breaks/ "“Responsive Line Breaks,” an article by Dan Mall")

## br要素にdisplay:noneを指定
まず、1つ目はbr要素にスタイルを充てる方法です。「display:none」を指定することで改行をなくします。例文では、スクリーンのwidthが480px以下になると改行がなくなるイメージです。

### HTML
	<p>これはbr要素を使用した際の例文です。<br class="br-sp">まず一つ目の改行位置の変更方法を紹介しています。</p>


### CSS
	@media screen and (max-width: 480px) {
		.br-sp { display:none; }
	}

## span要素でdisplayプロパティの値を切り替えて改行
2つめはspan要素にスタイルを充てる方法です。やや、HTMLの記述が面倒になります。この例文では、基本は「display:block」を指定することで擬似的に改行を作り、480px以下の際は「display:inline」を指定し、改行をなくしています。

<h3>HTML</3>
	<p><span class="br">これはspan要素を使用した際の例文です。</span><span class="br">2つ目の改行位置の変更方法を紹介しています。</span></p>

<h3>CSS</3>
	.br { display:block; }

	@media screen and (max-width: 480px) {
		.br { display:inline; }
	}

## 終わりに
2種類の方法をご紹介しましたが、基本的には前者の方法のほうがHTMLに余計な記述も増えずいいのかなと思ってます。特に難しいことではないので、一度試していただければ幸いです。

---
※この記事は WordPress に投稿した記事を変換したものです。一部不自然な表示があるかも知れません。ご了承ください。
