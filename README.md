# floating_banner
floating banner for site CVR (Web Design)

【ページの集客率UPを狙う！開閉式のフローティングバナーの作り方】

<b>サイトにおけるバナーの役割</b>

バナーは広告として、サイトを訪れた人を別のページやサイトに誘導するものとして、また訪問者が求めるページに辿り着きやすくするために使われ、基本的にページの一部に埋め込まれていることがほとんどです。

しかし、バナーが埋め込まれている状態(特にページ中部)では、訪問者がそのバナーに気付かず通り過ぎてしまったり、そのバナーまでたどり着かないこともあります。

<b>フローティングバナーのメリット</b>

フローティングバナーはページをスクロールしても、画面に固定表示されるので、ページを訪問した人の目に止まりやすくなります。

そのため、フローティングバナーを使うことで、そのサイトやページにより多くのユーザを引きつけることができます。

もちろん、アフィリエイト広告など、大々的に宣伝したいものでなければ、埋め込み式のバナーの方が良いですが、特に広告したいもの、ページの集客率をあげたいものに関してはフローティングバナーを使うのが効果的です。

しかし、そのページを何度も訪れる人や、その広告に興味がない人にとっては、スクロールに応じてついてくるフローティングバナーは邪魔に感じ、かえって逆効果になってしまうこともあります。

そこで、バナーを開閉式にすることで、そのデメリットを解消することができます。

今回はそんな閉開式のフローティングバナーのつくり方をご紹介します。

<b>フローティングバナーのつくり方</b>

まずは、単純なフローティングバナーのコード例を紹介します。

```html
<div class="floating-banner">
  <a href="サイトURL" target="_blank">
  <img src="バナー画像" style="width:400px;">
  </a>
</div>
```
```css
a:hover img {
  opacity:1;
  filter: alpha(opacity=80);
  -ms-filter: "alpha( opacity=80 )";
  transition: 0.4s;
}
.floating-banner {
  position: fixed;
  left: 0;
  bottom: 0;
  z-index: 99;
}
```

【実装例】
https://ozaki-hr8.github.io/floating_banner/

CSSでバナーの位置を固定することで簡単に実装することができます。

<b>開閉式のフローティングバナーのつくり方</b>

次に開閉式のフローティングバナーのコード例を紹介します。

```html
<div class="floating-banner">
<button onclick="changeClass()" class="floating-banner_button" role="button"></button>
<p class="target">
<a href="サイトURL" target="_blank">
<img src="バナー画像" style="width:400px;">
</a>
</p>
</div>
```
```js
<script type="text/javascript">
var $target = document.querySelector('.target')
var $button = document.querySelector('.floating-banner_button')
$button.addEventListener('click', function() {
$target.classList.toggle('is-hidden')
$button.classList.toggle('floating-banner_buttonClose')
})
</script>
}
```
```css
a:hover img {
  opacity:1;
  filter: alpha(opacity=80);
  -ms-filter: "alpha( opacity=80 )";
  transition: 0.4s;
}
.floating-banner {
  position: fixed;
  left: 0;
  bottom: 0;
  z-index: 99;
}
.target.is-hidden {
  display: none;
}
p {
  margin: 0;
}
/* ボタンの設定 */
.floating-banner_button {
  display: block;
  width: 30px;
  height: 30px;
  background-color: rgb(87,87,87);
  position: absolute;
  left: 92.5%;
  cursor: pointer;
}
/* アイコンの設定(開) */
.floating-banner_button::before, .floating-banner_button::after {
  display: block;
  content: '';
  width: 4px;
  height: 24px;
  background-color: #FFF;
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  margin: auto;
}
.floating-banner_button::before {
  transform: rotateZ(90deg);
}
.floating-banner_button::after {
  transform: rotateZ(90deg);
}
/* アイコンの設定(閉) */
.floating-banner_buttonClose {
  display: block;
  width: 30px;
  height: 30px;
  margin-left: auto;
  background-color: rgb(87,87,87);
  position: absolute;
  left: 0;
  bottom: 100%;
  cursor: pointer;
}
.floating-banner_buttonClose::before, .floating-banner_buttonClose::after {
  display: block;
  content: '';
  width: 4px;
  height: 24px;
  background-color: #FFF;
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  margin: auto;
}
.floating-banner_buttonClose::before {
  transform: rotateZ(0deg);
}
.floating-banner_buttonClose::after {
  transform: rotateZ(90deg);
}
}
```

【実装例】
./index.html

JavaScriptを用いて、ボタンがクリックされた時にバナーを非表示に、アイコンが変更されるようにしています。

ちなみにこのアイコンの設定としては、中に何も要素を持たないbuttonタグの:before要素と:after要素に対して縦長の四角形を設定しているため、初期状態では2本の縦線が重なっている状態になっています。

その2本の線それぞれを回転させることで、バナーの開閉に応じて、それぞれの図形を表現しています。

また、このアイコンはcontentの部分に矢印などの画像を挿入したりしてアレンジすることもできます。

是非参考にしてみてください。
