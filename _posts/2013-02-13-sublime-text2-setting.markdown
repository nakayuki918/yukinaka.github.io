---
layout: post
title: "'おすすめエディタSublime Text2の導入'と設定（初期設定編）"
published: true
date: 2013-02-13 09:58
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
愛用エディタSublime Text2の記事です。何番煎じか分からないですが、これから導入を考えている人などいたら、参考になれば幸いです。Mac限定のエディタなどが多い中、Windows,Mac,Linuxで動くように用意されているのは嬉しい限りですね。
余談ですが、使い始めた当初私は、Windowsをメインマシンとして使っておりエディタ難民と化していたので、Sublime Text2を使用した時は使いやすさに感動したとともに、Windows用も作ってくれてありがとうと感謝しましたw

## インストール
まず、公式サイトからダウンロードをしましょう。
[Sublime Text - Download](http://www.sublimetext.com/2 "Sublime Text - Download")

ダウンロードが完了したら、他のアプリケーションと同じようにインストールを開始しましょう。この段階では特に変わった操作などは必要としません。

## Package Controlのインストール
Sublime Text2には数多くの拡張機能があります。その拡張機能のインストールにPackage Controlは欠かせない存在となっています。デフォルトの状態では含まれていないので、まず一番にPackage Controlをインストールしましょう。

メニューからView＞Show Consoleを選択し、コンソールを開きます。

<img src="/img/2013/02/5d68d5a2fc26803324d8254a3afc2e27.png" alt="Sublime Text2のコンソールを選択"  class="alignnone size-full wp-image-166" />

コンソールが開かれたら以下のコードをコンソールに入力して下さい。エンターキーを押すとインストールが開始されます。


    import urllib2,os;pf='Package Control.sublime-package';ipp=sublime.installed_packages_path();os.makedirs(ipp) if not os.path.exists(ipp) else None;open(os.path.join(ipp,pf),'wb').write(urllib2.urlopen('http://sublime.wbond.net/'+pf.replace(' ','%20')).read())


<img src="/img/2013/02/5ee700d6a009ae3dd52ce49cff4fcc34.png" alt="コードを入力する場所" class="alignnone size-full wp-image-168" />

インストールが終わったら再起動しましょう。これでPackage Controlのインストールは完了です。

## 初期設定
Sublime Text2の設定はSublime Text2 ＞ Preferences ＞ Setting User から行います。基本的にそのままでも不自由はないかと思いますが、どうせなら自分好みに便利に使いたいのでお好みで以下のような記述をしてあげましょう。

    //フォントサイズの変更
    "font_size": 15,
    //選択している行をハイライト
    "highlight_line": true,
    //サイドバーに表示するフォルダ名を太字に
    "bold_folder_labels": true,
    //タブやスペースなどの不可視文字の表示
    "draw_white_space": "all",
    //折り返し(falseにするとスクロールバーの表示となります)
    "word_wrap": true,
    //インデントした際のサイズ
    "tab_size": 4,
    //キーバインドをVimのように
    "ignored_packages":[]

簡潔となってしまいましたが、以上となります。

## おわりに
ざっくりと導入から設定について記載しましたが、他にも色々な設定ができますので、一度自分好みになるように様々な設定を試してみてください。

なお、Sublime Text2はシェアウェアです。ダウンロード自体は無料ですが、継続して使う場合は購入が必要です。現在だとライセンス登録していれば、Sublime Text3のBeta版が使えるようです。

今回は設定のみを記事としましたが、次回は基本操作について書く予定です。よろしくお願いいたします。

### 参考サイト


- [”恋に落ちるエディタ”「Sublime Text」 完全入門ガイド！](http://liginc.co.jp/designer/archives/6774 "”恋に落ちるエディタ”「Sublime Text」 完全入門ガイド！")
- [Sublime Text2ってエディタがすごくイイ。Dreamweaverから乗り換えた時の初期設定とか使い方とかをメモ](http://mnemoniqs.com/web/sublimetext2/ "Sublime Text2ってエディタがすごくイイ。Dreamweaverから乗り換えた時の初期設定とか使い方とかをメモ")

---
※この記事は WordPress に投稿した記事を変換したものです。一部不自然な表示があるかも知れません。ご了承ください。
