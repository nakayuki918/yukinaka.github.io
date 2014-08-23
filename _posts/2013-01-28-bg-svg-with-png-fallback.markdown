---
layout: post
title: "背景画像でSVG形式の画像が表示できない際にPNG形式の画像を表示する方法(IE6・IE7・IE8用)"
published: true
date: 2013-01-28 07:53
comments: true
categories:
- CSS・CSS3
tags:
- CSS
- SVG
keywords:
- CSS・CSS3
- CSS
- SVG
type: post
---
SVG形式の画像の表示はInternet Explorerの場合、IE9以上でしか表示できません。IE6、IE7、IE8は基本的にはPNGやGIF形式の画像を表示することになります。次に書いていく方法で、JavaScriptを使わずにCSSのみで、IE9はSVG、IE6、IE7、IE8はPNGといった表示方法が可能です。
※但し背景画像に限ります。

参考サイト
[Cross-Browser CSS Technique for SVG Sprites with PNG Fallback](http://tobias.is/geeky/webperf/cross-browser-css-technique-for-svg-sprites-with-png-fallback/ "Cross-Browser CSS Technique for SVG Sprites with PNG Fallback")

## CSS3のrgba()を使ってIE6、IE7、IE8に代替画像を表示させる。

    .svg-or-png {
        background: url(img/hoge.png) no-repeat; /* for IE7 IE8 */
        background: rgba(0,0,0,0) url(img/hoge.svg) no-repeat; /* modern browser */
    }

上記の記述になります。
まず、backgroundでpngなどのIE6、IE7、IE8でも表示できる画像を指定します。次にCSS3のrgba()を指定し、背景画像にはsvgを指定します。

以上です。これでIE9未満はpng、それ以外はsvgが表示させることができます。IE9未満では、CSS3のrgba()がサポートされていないので、上記の2行目が無視されます。他のブラウザでは2行目の記述が認識され、1行目の記述が上書きされ2行目に指定した表示になります。

## 注意点：Android3.0未満では使えない
残念なことにAndroid3.0未満では、SVG形式の画像が表示することができません。そしてAndroidではrgba()が使えてしまうのでこの方法も使えないのです。

Android3.0未満では[Modernizr](http://modernizr.com/ "Modernizr")を利用するか、似たようにJSでsvg非対応用のクラスをつけるのがベターかと思います。

## 追記
記事の一部を修正しました。
IE7、IE8ではなく、IE9未満でした。IE6も対象に入ります。

---
※この記事は WordPress に投稿した記事を変換したものです。一部不自然な表示があるかも知れません。ご了承ください。
