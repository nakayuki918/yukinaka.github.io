---
layout: page
title: 【sample】リンクの領域を親のブロック要素全体にし、子要素のリンクは各リンク先へ飛ばす
permalink: /sample-link-entire-block-element/
---

##サンプル

<style scoped>
.jsc-caset:hover {
background: #ccc;
}
</style>
<div class="jsc-caset">
<a href="#all" class="jsc-title">全体</a>
<a href="#1">個別1</a>
<a href="#2">個別2</a>
</div>
<script src="//ajax.googleapis.com/ajax/libs/jquery/1.11.1/jquery.min.js"></script>
<script>
$(function(){
$('.jsc-caset a').click(function(event) {
event.stopPropagation();
});
$('.jsc-caset').click(function() {
location.href = $(this).find('.jsc-title').attr('href');
});
});
</script>