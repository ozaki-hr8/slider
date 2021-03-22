# slider
'slick' slider plug-in for site information (Web Design)

【jQueryライブラリ「slick」を使ったレスポンシブなスライダーの導入方法】

セール情報などのお知らせを表示するために、自社サイトにスライダーを表示させたいという方は多いかと思います。
スライダーを実装するためのライブラリには様々なものがありますが、今回は、簡単にレスポンシブ表示のできる人気のプラグイン「slick」を使ったスライダーの実装をご紹介します。

まずは以下のURLへ行き、「get it now」→「Download Now」をクリックして、slickをローカルにダウンロードしていきます。(cdnでも可)

https://kenwheeler.github.io/slick/

ダウンロードしたフォルダーから「slick」という名前のフォルダを、表示させたいhtmlファイルが入ったフォルダに移動させます。

<img width="1440" alt="folder-1" src="https://user-images.githubusercontent.com/69960076/111946273-831e1a80-8b1e-11eb-930c-995f9880a3b5.png">

次に、htmlファイルとcssファイルを変更していきます。

```html
<html>
  <head>
    <title>Responsive Slider</title>
    <meta charset="utf-8">
    <link rel="stylesheet" type="text/css" href="slick/slick.css"/>
    <link rel="stylesheet" type="text/css" href="slick/slick-theme.css"/>
  </head>
  <body>
    <section class="next slider">
      <div><img src="img/sample1.png"></div>　
      <div><img src="img/sample2.png"></div>　
      <div><img src="img/sample3.png"></div>　
      <div><img src="img/sample4.png"></div>　
      <div><img src="img/sample5.png"></div>　
      <div><img src="img/sample6.png"></div>　
    </section>
    <script src="https : //code.jquery.com/jquery-2.2.0.min.js" type="text/javascript"></script>
    <script type="text/javascript" src="slick/slick.min.js"></script>
  </body>
</html>
```
```css
<style>
  html, body {
    margin :  0;
    padding :  0;
  }
 
  * {
    box-sizing :  border-box;
  }
 
  .slider {
      width :  50%;
      margin :  100px auto;
  }
 
  .slick-slide {
    margin :  0px 20px;
    height : auto;
  }
 
  .slick-slide img {
    width :  100%;
  }
 
  .slick-prev : before,
  .slick-next : before {
    color :  black;
  }
 
 
  .slick-slide {
    transition :  all ease-in-out .3s;
    opacity :  .2;
  }
 
  .slick-active {
    opacity :  .5;
  }
 
  .slick-current {
    opacity :  1;
  }
</style>
```

これでslickの設定は完了です。ヘッダーの中で、先程ダウンロードしたslickフォルダの中のCSSコードとリンクさせ、bodyタグの直前で、jQueryを読み込み、JSコードとリンクさせています。

スライダーに画像を使う場合はimgタグを並べ、その他の場合はdivタグなどを並べ、任意のクラスを指定した箱を作ります。(sectionでなくても構いません)

styleタグで囲んだCSSコードはなくても構いませんが、スライダーに指定する画像サイズによっては、レスポンシブの表示が崩れることがあるので、

```css
.slick-slide {
    height : auto;
  }
```
  
は設定しておきましょう。

次に、実際にslickを使ってスライダーを表示させるために、bodyタグの直前に次のjsコードを挿入します。

```js
<script type="text/javascript">
$(document).on('ready', function() {
$('.next').slick({
      slidesToShow :  1,
      slidesToScroll :  1,
      dots :  true,
      centerMode :  true,
      focusOnSelect :  true
});
});
</script>
```
このJSコードを改変するだけで、様々なスライダーを作成することが可能になります。
いくつか、サンプルもご紹介しておきます。

スライダーに使用する画像が入ったタグに指定したクラス名(ここではnext)をJS内で呼び出し、スライダーの表示に関わる設定をしています。

また、スライダーの主な設定項目は以下のようになっています。

| JSコード                | 設定項目                                                                        | 
| ----------------------- | ------------------------------------------------------------------------------- | 
| dots : true/false       | ドットのナビを表示/非表示                                                       | 
| slidesToShow : 1        | 表示スライド数                                                                  | 
| autoplay : true/false   | スライドの自動再生                                                              | 
| autoplaySpeed : 2000    | 自動再生の速さ(ms)                                                              | 
| arrows : true/false     | 矢印のナビを表示/非表示                                                         | 
| speed : 300             | スライドの速さ(ms)                                                              | 
| infinite : true/false   | 最後のスライドの次に最初のスライドを表示する/最後のスライダーでスライドを止める | 
| fade : true/false       | スライドのフェード表示                                                          | 
| centerMode : true/false | 前後のスライドの表示                                                            | 

先ほどのJSコードで作成したスライダーは次のようなものになります。

<section class="next slider">
<div><img src="/img/hr/sample1.png"></div>
<div><img src="/img/hr/sample2.png"></div>
<div><img src="/img/hr/sample3.png"></div>
<div><img src="/img/hr/sample4.png"></div>
<div><img src="/img/hr/sample5.png"></div>
<div><img src="/img/hr/sample6.png"></div>
</section>
