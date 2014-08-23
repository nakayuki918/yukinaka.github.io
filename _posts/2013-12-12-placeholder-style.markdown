---
layout: post
title: "HTML5のplaceholder属性を使用したプレースホルダのスタイルを調整する"
published: true
date: 2013-12-12 12:12
comments: true
categories:
- CSS・CSS3
tags:
- CSS
keywords:
- CSS・CSS3
- CSS
type: post
---
下記の記述でプレースホルダを中央寄せにしてたのですが、Androidで適用されない端末があるようです。



	input[type=&quot;text&quot;] {
		text-align: center;
	}



色々調べたらplaceholderそのものにスタイルを当てる方法がありました。
細かい検証ができていないのですが、基本的には以下の記述で変更可能と思われます。



	::-webkit-input-placeholder {
		color: #AAA;
		text-align:center;
	}

	:-moz-placeholder { /* Firefox 18- */
		color: #AAA;
		text-align:center;
	}

	::-moz-placeholder {  /* Firefox 19+ */
	   color: #AAA;
	   text-align:center;
	}

	:-ms-input-placeholder {
		color: #AAA;
		text-align:center;
	}



参考URL:[Style Placeholder Text](http://css-tricks.com/snippets/css/style-placeholder-text/ "Style Placeholder Text")

---
※この記事は WordPress に投稿した記事を変換したものです。一部不自然な表示があるかも知れません。ご了承ください。
