---
layout: post
title:  "リンクの領域を親のブロック要素全体にし、子要素のリンクは各リンク先へ飛ばす方法"
date:   2014-07-21
type: post
---

タイトルが散々なんですが(思いつかなかった)、処理を見てもらえればなんとなく言いたいことは分かると思うので許して欲しい。
以下が具体的なHTMLとJavaScriptの記述になる。

## HTML

HTMLは下記の通り。親となる`.jcs-link-wrap`をクリックすると`#all`に移動し、各a要素はそれぞれのリンク先に移動するという仕様。

    <div class="jsc-link-wrap">
        <a href="#all" class="jsc-link">全体</a>
        <a href="#1">個別1</a>
        <a href="#2">個別2</a>
     </div>

## JavaScript

JavaScriptは以下のようになる。
`.jsc-link-wrap`をクリックすると、子要素にある`.jsc-link`のhref属性の値を引っ張ってきてそちらへ移動させる。  
各リンクをクリックすると、`stopPropagation()`でイベント伝播をキャンセルしてくれるので、`.jsc-link-wrap`をクリックした時の処理は発生せず、それぞれのリンクへ移動するようになる。

    $(function(){
        $('.jsc-link-wrap a').click(function(event) {
            event.stopPropagation();
        });
        $('.jsc-link-wrap').click(function() {
            location.href = $(this).find('.jsc-link').attr('href');
        });
     });

サンプルではすべて`#`にしてるので分かりにくいが、ブラウザのURL欄を見てもらえると、しっかりとそれぞれの値に変わっているのが分かると思う。

[サンプル](/sample-link-entire-block-element)