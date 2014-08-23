---
layout: post
title: "ページネーションのような大きさが定まらないブロック要素の固まりを中央配置にする方法"
published: true
date: 2013-02-05 08:19
comments: true
categories:
- CSS・CSS3
tags:
- CSS
- "テクニック"
keywords:
- CSS・CSS3
- CSS
- "テクニック"
type: post
---
よくあるセンタリングの方法として、ブロック要素にwidthを指定してmargin-left:auto;margin-right:auto;で中央に置くのが一般的ですが、ページネーションのような大きさの定まらない要素には使えません。ここでは2種類の方法を紹介します。

## text-align:centerとdisplay:inline-blockを使う
### HTML【ページネーション(ページャー)】

    <div class="tac">
        <ul class="pagination">
            <li><a href="#">1</a></li>
            <li><a href="#">2</a></li>
            <li><a href="#">3</a></li>
            <li><a href="#">4</a></li>
            <li><a href="#">5</a></li>
        </ul>
    </div>

### CSS

    .tac {
        text-align: center;
    }
    .pagination {
        display: inline-block;
        *display:inline;
        zoom:1;
    }

display:inline-blockは、インライン要素でありながら、widthやheightを指定できるプロパティです。親要素にtext-align:centerを指定することで、inline-blockの指定されたpaginationが中央に配置されます。*display:inlineとzoom:1はIE6,IE7対策です。不要であればとりましょう。これが一つ目の方法です。

## display:tableとmargin-left:auto;margin-right:auto;
### HTML【ページネーション(ページャー)】

    .tac {
        text-align: center;
    }
    .pagination {
        display: inline-block;
        *display:inline;
        zoom:1;
    }

### CSS

    .pagination {
        display: table;
        margin-left:auto;
        margin-right:auto;

display:tableはdisplay:table-cellと合わせてスマートフォンページの制作などでよく使うプロパティの一つです。指定した要素をtable要素と同じようにします。ブロック要素となり、幅が自動で確保されるため、margin:0 auto;のような指定をすることで、中央に配置することができます。

ただし、display:tableはCSS2のプロパティですので、残念ながらIE7以下は非対応です。その場合は先のdisplay:inline-blockの方法を使うのがいいでしょう。

---
※この記事は WordPress に投稿した記事を変換したものです。一部不自然な表示があるかも知れません。ご了承ください。
