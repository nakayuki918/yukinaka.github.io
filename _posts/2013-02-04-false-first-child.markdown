---
layout: post
title: "よくある:first-child擬似クラスの間違い"
published: true
date: 2013-02-04 01:48
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
ul li:first-childとかでよく使用すると思われる、first-child擬似クラスですが、親要素の中の<em>特定の最初の要素</em>にかかるわけではありません。あくまで**子要素の最初の要素**です。dlを例に見て行きましょう。


## first-childが効くのは最初の子要素

### HTML

    <dl>
        <dt>タイトル</dt>
        <dd>説明</dd>
    </dl>

### CSS

    dl dd:first-child {
        font-weight:bold;
    }


上記のような例では、first-childは効きません。親であるdlの中のfirst-childはdtだからです。ddは最初の子要素ではないので、対象から外れます。

このようなパターンでCSSのみで完結させたいのであれば、隣接セレクタやCSS3のnth-childあたりを使って対応しましょう。

---
※この記事は WordPress に投稿した記事を変換したものです。一部不自然な表示があるかも知れません。ご了承ください。
