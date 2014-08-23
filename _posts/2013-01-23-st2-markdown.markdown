---
layout: post
title: "マークダウン記法で書かれたものを表示するSublimeText2のパッケージMarkdown Preview"
published: true
date: 2013-01-23 09:55
comments: true
categories:
- "ツール"
tags:
- Sublime Text 2
- "エディタ"
- "ツール"
keywords:
- "ツール"
- Sublime Text 2
- "エディタ"
- "ツール"
type: post
---
マークダウン記法で書かれたものを表示するツールはたくさんありますが、愛用しているエディタSublime Text2で完結させたかったので、Markdown Previewというパッケージを使用しています。

以下のページを参考にさせていただきました。

[コードで一言: SublimeText2でMarkdownをプレビューするプラグイン](http://codedehitokoto.blogspot.jp/2012/04/sublimetext2markdown.html "コードで一言: SublimeText2でMarkdownをプレビューするプラグイン")

## Markdown Previweの使用方法
まず、cmd(ctrl)+shift+pでinstall packageを選択し、該当するパッケージをインストールしましょう。
次に、他のキーバインドと競合しないように、キーバインドを自分の使い安いに変更しましょう。

    [ { "keys": ["alt+m"], "command": "markdown_preview", "args": {"target": "browser"} }]

僕は、参考サイト通りにalt+mを指定しています。

基本的な準備は以上です。あとはST2でマークダウン記法で記述し、先に指定したalt+ｍを入力すると、ブラウザ上でプレビューしてくれます。

デフォルトのCSSを編集したい場合は、
Preferences > Package Settings > Markdown Preview > Setting-Default(Setting-user) を選択し、以下の画像で指している部分に、指定するCSSへの絶対パスを記載してあげましょう。

<img src="/img/2013/01/md.png" alt="Sublime Text2 マークダウンのCSSのパス指定箇所" width="910" height="152" class="alignnone size-full wp-image-107" />

以上となります。
マークダウン記法はメモや議事録を取るのに非常に便利なので、使用したことない方は是非これを機に使ってみて下さい。

---
※この記事は WordPress に投稿した記事を変換したものです。一部不自然な表示があるかも知れません。ご了承ください。
