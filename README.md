# slider
'slick' slider plug-in for site information(Web Design)

【導入方法】
セール情報などのお知らせを表示するために、自社サイトにスライダーを表示させたいという方は多いかと思います。
スライダーを実装するためのライブラリには様々なものがありますが、今回は、簡単にレスポンシブ表示のできる人気のプラグイン「slick」を使ったスライダーの実装をご紹介します。

まずは以下のURLへ行き、「get it now」→「Download Now」をクリックして、slickをローカルにダウンロードしていきます。(cdnでも可)
https://kenwheeler.github.io/slick/

ダウンロードしたフォルダーから「slick」という名前のフォルダを、表示させたいhtmlファイルが入ったフォルダに移動させます。

次に、このフォルダ内にあるhtmlファイルの内容をサイトに組み込めば、slickの設定は完了です。ヘッダーの中で、先程ダウンロードしたslickフォルダの中のCSSコードとリンクさせ、bodyタグの直前で、jQueryを読み込み、JSコードとリンクさせています。

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

dots : true/false	ドットのナビを表示/非表示
slidesToShow : 1	表示スライド数
autoplay : true/false	スライドの自動再生
autoplaySpeed : 2000	自動再生の速さ(ms)
arrows : true/false	矢印のナビを表示/非表示
speed : 300	スライドの速さ(ms)
infinite : true/false	最後のスライドの次に最初のスライドを表示する/最後のスライダーでスライドを止める
fade : true/false	スライドのフェード表示
centerMode : true/false	前後のスライドの表示
