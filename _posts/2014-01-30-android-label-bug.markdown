---
layout: post
title: "Androidでinput要素とlabel要素を紐付けた際のバグ"
published: true
date: 2014-01-30 10:00
comments: true
categories:
- HTML・HTML5
tags:
- Android
keywords:
- HTML・HTML5
- Android
type: post
---
バグなのか仕様なのかよく分かりませんが、Androidでlabel要素とinput要素を紐付け、入力フィールドにフォーカスした際にlabel内のテキストが入力フィールド反映されてしまうという事象が起きました。
なお、簡略的にinput要素と説明していますが、実際にはテキストを入力できる要素全てにあたります(textarea、input type="tel"など)。

説明だけでは分かりづらいので具体的な画像とともに説明していきます。


## 具体例

最初の状態です。プレースホルダーを指定していますが、特にあってもなくても変わりません。なお、端末は【GALAXY SⅡ WiMAX ISW11SC】を使用しています。
HTMLは下のようなものとなります。

<img style="display:block" src="/img/2014/01/android.label1_.png" alt="状態が起きる前のアンドロイド端末の様子" width="276" height="531" class="alignnone wp-image-446">

    <label for="test">テスト</label>
    <input type="text" id="test" placeholder="ラベルバグ">

次にフォーカスした状態です。ラベル内の内容が入力フィールドに反映されているのが分かります。

<img style="display:block" src="/img/2014/01/android.label2_.png" alt="テキストフィールドにフォーカスした際のAndroidの様子" width="276" height="531" class="alignnone wp-image-451">

文字を入力し始めるとフィールドに反映されていた文字も消えます。

<img style="display:block" src="/img/2014/01/android.label3_.png" alt="文字を入力し始めた様子" width="276" height="531" class="alignnone wp-image-453">

以上のような事象が起きます。続いて対策を記述したいと思います。

## 対策

結論から言ってしまうと、色々試しましたが、完全な解決策はありませんでした。強いて言うなら紐付けをやめるのが一番の対策になります。

海外のサイトに以下のCSSを指定すれば対策可能という記述がありましたが、どうやら日本語(マルチバイト？)の入力ができなくなるのでダメでした。

参考URL:[http://www.bielousov.com/2012/android-label-text-appears-in-input-field-as-a-placeholder/](http://www.bielousov.com/2012/android-label-text-appears-in-input-field-as-a-placeholder/ "http://www.bielousov.com/2012/android-label-text-appears-in-input-field-as-a-placeholder/")

inputmode属性でkanaを指定しても全く変わりません。

    input[type="text"] {
        -webkit-user-modify: read-write-plaintext-only;
    }

フォーカスしている状態ですが、最初から英字が選択されているのが分かると思います。

<img style="display:block" src="/img/2014/01/android.label4_.png" alt="-webkit-user-modify: read-write-plaintext-only;を指定したテキストフィールド" width="276" height="531" class="alignnone wp-image-457">

ちなみにAndroid Browserではなく、Chromeで確認したところlabelの内容が入力フィールドに反映されるという現象は起きませんでした。端末が違いますが、以下の画像です。
端末は【Xpria Z1 SO-01F】を使用しています。

<img style="display:block" src="/img/2014/01/android.label5_.png" alt="Chromeで確認した様子" width="324" height="626" class="alignnone wp-image-459">

## おわりに
Androidはすべての事象に対応しようとするとキリがないので、ある程度の妥協は必要不可欠です。ユーザーの操作を阻害しないレベルの致命的でないものであれば個人的には許容していくほうがコスト等考えた上でみんな幸せになれると思います。

状況に応じて適切な判断をしましょう。

なお、検証にはRemote Testkitを使用しました。

---
※この記事は WordPress に投稿した記事を変換したものです。一部不自然な表示があるかも知れません。ご了承ください。
