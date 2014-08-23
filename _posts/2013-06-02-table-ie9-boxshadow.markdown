---
layout: post
title: "IE9でtable内でbox-shadowが表示されない場合の対策"
published: true
date: 2013-06-02 00:30
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
IE9でtable内の要素にbox-shadowが指定されていると表示されない場合があります。原因はtableに「border-collapse:collapse;」の指定があることが原因です。
tableにかかっている「border-collapse: separate;」に変更すれば問題は解決しますが、デザイン上難しい場合が多いと思います。代わりに以下のような方法で解決可能です。

## box-shadowがかかっている要素にborder-collapse:separateを指定

	.box {
		box-shadow:0 1px 0 1px #666;
		border-collapse:separate;
	}

tableにcollapseの指定をせずとも、該当する要素に直接指定することで解決できます。

参考サイト: <a href="http://stackoverflow.com/questions/5617455/box-shadow-on-ie9-doesnt-render-using-correct-css-works-on-firefox-chrome" >box-shadow on IE9 doesn't render using correct CSS, works on Firefox, Chrome</a>

---
※この記事は WordPress に投稿した記事を変換したものです。一部不自然な表示があるかも知れません。ご了承ください。
