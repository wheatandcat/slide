---
# try also 'default' to start simple
theme: default
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: https://source.unsplash.com/collection/94734566/1920x1080
# apply any windi css classes to the current slide
class: "text-center"
# https://sli.dev/custom/highlighters.html
highlighter: shiki
# show line numbers in code blocks
lineNumbers: false
# some information about the slides, markdown enabled
info: |
  ## 右手が腱鞘炎になったエンジニアを支える技術
# persist drawings in exports and build
drawings:
  persist: false
title:  右手が腱鞘炎になったエンジニアを支える技術
layout: intro
colorSchema: "light"
---

## 右手が腱鞘炎になったエンジニアを支える技術

<div class="flex justify-center">
  <img
    class="w-30 pt-2"
    src="/logo.svg"
  />
</div>

<div class="pt-12">
  <span @click="$slidev.nav.next" class="px-2 py-1 rounded cursor-pointer" hover="bg-white bg-opacity-10">
    Press Space for next page <carbon:arrow-right class="inline"/>
  </span>
</div>

<div class="abs-br m-6 flex gap-2">
  <button @click="$slidev.nav.openInEditor()" title="Open in Editor" class="text-xl icon-btn opacity-50 !border-none !hover:text-white">
    <carbon:edit />
  </button>
  <a href="https://github.com/slidevjs/slidev" target="_blank" alt="GitHub"
    class="text-xl icon-btn opacity-50 !border-none !hover:text-white">
    <carbon-logo-github />
  </a>
</div>

<!--
The last comment block of each slide will be treated as slide notes. It will be visible and editable in Presenter Mode along with the slide. [Read more in the docs](https://sli.dev/guide/syntax.html#notes)
-->

---

<div class="flex pb-5">
  <div class="px-5">
    <div class="rounded-full bg-white w-30 h-30 overflow-hidden border-2 border-black border-dotted border-opacity-20">
      <img
        class="w-40 pt-2"
        src="/account.png"
      />
    </div>
  </div>
  <div class="mt-11">
    <h2><b>自己紹介</b></h2>
  </div>
</div>
<br />
<br/>

- 📝 飯野陽平（[wheatandcat](https://github.com/wheatandcat)）
- 🏢 フリーランスエンジニア（シェアフル株式会社CTO）
- 💻 Blog: https://www.wheatandcat.me/
- 🛠 今までに作ったもの
  - [memoir](https://memoir-lp-mvbeacmwe-wheatandcat.vercel.app/)
  - [ペペロミア](https://peperomia.app/)
  - [Atomic Design Check List](https://atomic-design-checklist.vercel.app/)

<style>
ul {
  padding-left: 1rem;
  margin-top: 0.1rem;
}
li {
  color: #696969;
  @apply font-500;
  font-size:1.15rem;
}
a {
  color: #84b9cb;
  @apply font-500;
}
</style>


---

# **腱鞘炎**とは

<br/>

<div class="flex w-full">
<div class="w-120">


- 筋肉と骨を結びつけているものが**腱**
- **腱鞘**は腱が骨から離れないように押さえつける組織
- 指を動かすことで、**腱**と**腱鞘**が擦れて炎症が起きてしまうのが**腱鞘炎**
- なので、指を曲げたり、手首を動かしたりすると**激痛が走る**

</div>

<div>
  <img
    class="w-50 pt-10 pl-10"
    src="/img_001.png"
  />
</div>
</div>

<style>
a {
  color: #84b9cb;
  @apply font-500;
}

p {
  margin: 1rem !important;
}

div {
  color: #4d4c61;
}

span {
  font-size:0.5rem;
  line-height: 0.5rem !important;
}

strong {
  color: #1f3134;
}

ul {
  padding-left: 1rem;
  margin-top: 0.1rem;
}

li {
  @apply font-500;
  margin-top: 0.25rem;
  
}
</style>

---

# 腱鞘炎になると、どうなるのか？

<br/>

<br/>

<div class="flex w-full">
<div class="w-120">


- キーボードを打鍵すると激痛
- マウスを動かすと激痛
- 炎症なので、動かすほど酷くなるので腕を使わないことが一番の回復方法
- でも、右手を使わずに作業するのは難しい

</div>

<div>
  <img
    class="w-50 pt-10 pl-10"
    src="/img_002.svg"
  />
</div>
</div>


<style>
a {
  color: #84b9cb;
  @apply font-500;
}

p {
  margin: 1rem !important;
}

div {
  color: #4d4c61;
}

span {
  font-size:0.5rem;
  line-height: 0.5rem !important;
}

strong {
  color: #1f3134;
}

ul {
  padding-left: 1rem;
  margin-top: 0.1rem;
}

li {
  @apply font-500;
}
</style>


---
layout: center
class: "text-center"
---

<div class="flex justify-items-center items-center flex-col"> 
  <div class="text-2xl font-700 text-enter w-full pt-10">
    <div>どうすれば、腱鞘炎の負荷を下げて<br/>作業ができるか研究してみた</div>
  </div>

  <img
    class="w-70"
    src="/img_003.svg"
  />
</div>


<style>
.main {
  display: flex;
  height: 80%;
  width: 100%;
  justify-content: center;
  align-items: center;
  color: #46AE35;
}
</style>


---
layout: image
image: '/before.png'
---
# Before セットアップ



<style>
a {
  color: #84b9cb;
  @apply font-500;
}

p {
  margin: 1rem !important;
}

div {
  color: #4d4c61;
}

span {
  font-size:0.5rem;
  line-height: 0.5rem !important;
}

strong {
  color: #1f3134;
}

ul {
  padding-left: 1rem;
  margin-top: 0.1rem;
}

li {
  @apply font-500;
}
</style>


---
layout: image-right
image: '/before.png'
---
# Before セットアップ

<br/>

 - キーボード
   - Magic Keyboard
 - マウス
   - MXV1s MX Vertical (ロジクール)
 - パームレスト有り

<v-click>
<div class="red">

→ 腱鞘炎になって分かったこと。
 - Magic Keyboardはストロークが浅いので腱鞘炎だとめっちゃ痛い
 - エレゴノミクス系のマウスは親指の腱鞘炎だと痛い
 - マウス自体も重めなので手首に負担がかかる
 - ダブルクリックが辛い
 - 左手で使用できない

</div>
</v-click>


<style>
a {
  color: #84b9cb;
  @apply font-500;
}

p {
  margin: 1rem !important;
}

div {
  color: #4d4c61;
}

.red {
  color: rgb(239 68 68);
}

span {
  font-size:0.5rem;
  line-height: 0.5rem !important;
}

strong {
  color: #1f3134;
}

ul {
  padding-left: 1rem;
  margin-top: 0.1rem;
  font-size:0.9rem;
}

li {
  @apply font-500;
}
</style>


---
layout: center
class: "text-center"
---

<div class="flex justify-items-center items-center flex-col"> 
  <div class="text-2xl font-700 text-enter w-full pt-10">
    <div>Version 1</div>
    <div>右腕が、ほぼ使えない時</div>
  </div>
  <br/>

  <img
    class="w-40"
    src="/img_004.svg"
  />
</div>


<style>
.main {
  display: flex;
  height: 80%;
  width: 100%;
  justify-content: center;
  align-items: center;
  color: #46AE35;
}
</style>

---
layout: image
image: '/version1.png'
---
# Version 1


---
layout: image-right
image: '/macair.png'
---
# Version 1

<br/>

 - **M2 MacBook Air**
   - 腱鞘炎になるとカーソル移動が大きくなれば、なるほどキツくなる
   - 小さい画面で作業できるAirが作業しやすかった
   - 2画面欲しい場合は[ユニバーサルコントロール](https://support.apple.com/ja-jp/HT212757)を使用してiMacに接続してSlackのみ表示で対応
 - **トラックパッドは左手で操作**
   - 基本左手で操作
   - ただドラックや範囲指定は両手が必要なので注意
 - **日本語は基本音声入力で対応**
   - 精度が高いので、現状もslackの返信等で使用している
   - ただ、英語と日本語が交じると意味不明な文章になるので使用する単語に注意が必要

<style>
a {
  color: #84b9cb;
  @apply font-500;
}

p {
  margin: 1rem !important;
}

div {
  color: #4d4c61;
}

span {
  font-size:0.5rem;
  line-height: 0.5rem !important;
}

strong {
  color: #1f3134;
}

ul {
  padding-left: 1rem;
  margin-top: 0.1rem;
  font-size:0.8rem;
}

li {
  @apply font-500;
}
</style>


---
layout: image-right
image: '/pedal.png'
---
# Version 1

<br/>

 - **Stream Deck Pedal**
   - フットペダルデバイス
   - 専用アプリで3ボタンのアクションを設定できる
   - かなり汎用的に設定が可能
   - 詳しくは以下を参照
   - https://www.elgato.com/ja/stream-deck-pedal
 - 基本1画面なので[Mission Control](https://support.apple.com/ja-jp/HT204100)をペダルに設定して操作
   - 腱鞘炎だと右手が使えないのでショートカットが押せないのと、3本指スワイプは手首の負担がでかいので、かなり助かった 👌
   - 現在も普通に使用しているくらい気に入っている

<style>
a {
  color: #84b9cb;
  @apply font-500;
}

p {
  margin: 1rem !important;
}

div {                       
  color: #4d4c61;
}

span {
  font-size:0.5rem;
  line-height: 0.5rem !important;
}

strong {
  color: #1f3134;
}

ul {
  padding-left: 1rem;
  margin-top: 0.1rem;
  font-size:0.8rem;
}

li {
  @apply font-500;
}
</style>


---
layout: center
class: "text-center"
---

<div class="flex justify-items-center items-center flex-col"> 
  <div class="text-2xl font-700 text-enter w-full pt-10">
    <div>Version 2（現状）</div>
    <div>右腕に負荷を軽減して作業</div>
  </div>
  <br/>

  <img
    class="w-20"
    src="/img_005.svg"
  />
</div>


<style>
.main {
  display: flex;
  height: 80%;
  width: 100%;
  justify-content: center;
  align-items: center;
  color: #46AE35;
}
</style>

---
layout: image
image: '/version2.png'
---
# Version 2


---
layout: image-right
image: '/version2.png'
---
# Version 2

<br/>

 - **REALFORCE for Mac**
   - キーストロークが深く、打鍵が軽いので腱鞘炎でも痛くない 👍
 - **Magic Trackpad**
   - iMacでも左手で操作できるように使用
   - ただドラックや範囲指定は両手必要なので注意
   - 使用感は正直Mac Airの方が良い気がする
 - 以下のソフトを使ってカスタマイズして操作を軽減
   - [カーソルセンス](https://plentycom.jp/cursorsense/)
     - できるだけ最小限の動作でカーソルを動かしたいので移動のスピードをカスタマイズ
   - [BetterTouchTool](https://folivora.ai/)
     - Trackpadの四隅のクリックにアクションを設定したり、4本指スワイプにアクションを設定できる

<style>
a {
  color: #84b9cb;
  @apply font-500;
}

p {
  margin: 1rem !important;
}

div {
  color: #4d4c61;
}

span {
  font-size:0.5rem;
  line-height: 0.5rem !important;
}

strong {
  color: #1f3134;
}

ul {
  padding-left: 1rem;
  margin-top: 0.1rem;
  font-size:0.8rem;
}

li {
  @apply font-500;
}
</style>



---
layout: image-right
image: '/mk2.png'
---
# Version 2

<br/>

 - **Stream Deck MK.2**
   - さまざまなアクションを設定できる左手デバイス
   - 物理ボタンの背景がディスプレイになっていて自由にカスタマイズができる
   - これを使うことでデュアルデスプレイの右側はカーソルを移動させずに操作ができる
    - Slack、Todoなどのアプリを表示
    - 組み合わせでChromeのタブ移動もできる
    - [Alfred](https://www.alfredapp.com/)や[Raycast](https://www.raycast.com/)と組み合わせれば基本どんな操作でも可能
 - 詳しくは、こちらを参照
   - https://www.elgato.com/ja/stream-deck-mk2

<style>
a {
  color: #84b9cb;
  @apply font-500;
}

p {
  margin: 1rem !important;
}

div {
  color: #4d4c61;
}

span {
  font-size:0.5rem;
  line-height: 0.5rem !important;
}

strong {
  color: #1f3134;
}

ul {
  padding-left: 1rem;
  margin-top: 0.1rem;
  font-size:0.8rem;
}

li {
  @apply font-500;
}
</style>

---
layout: center
class: "text-center"
---

<div class="flex justify-items-center items-center flex-col"> 
  <div class="text-2xl font-700 text-enter w-full pt-10">
    <div>Version Future（未来）</div>
    <div>今後のための実験的な試み</div>
  </div>
  <br/>

  <img
    class="w-60"
    src="/img_006.svg"
  />
</div>


<style>
.main {
  display: flex;
  height: 80%;
  width: 100%;
  justify-content: center;
  align-items: center;
  color: #46AE35;
}
</style>


---
layout: image
image: '/version3.png'
---
# Version Future


---
layout: image-right
image: '/ergodox.png'
---
# Version Future

<br/>

 - **ErgoDox EZ**
   - セパレート式メカニカルキーボード
   - 両腕のホームポジションが固定されないので胸を張った状態で打鍵できるので肩が凝りづらい
   - ストロークも深く、打鍵も軽い
   - キーボードの配置は自由にカスタマイズ可能
   - 購入時にいろいろ好みにカスタマイズが可能
   - ただ普通のキーボードとは大分打ち方がかわるので練習が必要
   - 現在は仕事以外で使用して練習中 🏃
 - 詳しくは、こちらを参照
   - https://ergodox-ez.com/

<style>
a {
  color: #84b9cb;
  @apply font-500;
}

p {
  margin: 1rem !important;
}

div {
  color: #4d4c61;
}

span {
  font-size:0.5rem;
  line-height: 0.5rem !important;
}

strong {
  color: #1f3134;
}

ul {
  padding-left: 1rem;
  margin-top: 0.1rem;
  font-size:0.8rem;
}

li {
  @apply font-500;
}
</style>


---
layout: image-right
image: '/kensington.png'
---
# Version Future

<br/>

 - **Kensington ExpertMouse**
   - トラックボールマウス
   - トラックボールをコロコロしてカーソル移動
   - 腕への負担が、ほぼ掛からない
   - ソフト側で⌘を押しながら移動時でカーソルの移動速度を変えられるので、一気に移動したい場合と細かく動かしたい場合の両方の動作に対応できる
   - ボタンが4つあるので、ダブルクリックなども割り当てられる
   - スクロールはトラックボールの周りのダイヤルをひねると移動
   - 腱鞘炎対策のマウスでは一番オススメ
 - 詳しくは、こちらを参照
   - https://ergodox-ez.com/

<style>
a {
  color: #84b9cb;
  @apply font-500;
}

p {
  margin: 1rem !important;
}

div {
  color: #4d4c61;
}

span {
  font-size:0.5rem;
  line-height: 0.5rem !important;
}

strong {
  color: #1f3134;
}

ul {
  padding-left: 1rem;
  margin-top: 0.1rem;
  font-size:0.8rem;
}

li {
  @apply font-500;
}
</style>


---
layout: image-right
image: '/tobii.png'
---
# Version Future

<br/>

 - **Tobii Eye Tracker 5**
   - 今回紹介するガジェットで一番未来 
   - 視線トラッカーデバイス
   - 基本的にはゲーム用途のデバイスだが、[Talon](https://talonvoice.com/)というプロジェクトと組み合わせることでフリーハンドでPCが操作可能になる
   - 仕事で使用するのは流石に無理そうだけど、**Talon**のSpeech APIも使いこなせれば、完全フリーハンドでネットサーフィンくらいはできるようになりそう
   - ただ、Speech APIは発音が厳しいのでネイティブじゅないと辛そう 😓
   - 一応デモをやってみる
 - 詳しくは、こちらを参照
   - https://gaming.tobii.com/product/eye-tracker-5/
   - https://www.joshwcomeau.com/blog/hands-free-coding/

<style>
a {
  color: #84b9cb;
  @apply font-500;
}

p {
  margin: 1rem !important;
}

div {
  color: #4d4c61;
}

span {
  font-size:0.5rem;
  line-height: 0.5rem !important;
}

strong {
  color: #1f3134;
}

ul {
  padding-left: 1rem;
  margin-top: 0.1rem;
  font-size:0.8rem;
}

li {
  @apply font-500;
}
</style>


---
layout: center
class: "text-center"
---

<div class="flex justify-items-center items-center flex-col"> 
  <div class="text-2xl font-700 text-enter w-full pt-10">
    <div>まとめ</div>
  </div>
  <br/>

  <img
    class="w-40"
    src="/img_007.svg"
  />
</div>


<style>
.main {
  display: flex;
  height: 80%;
  width: 100%;
  justify-content: center;
  align-items: center;
  color: #46AE35;
}
</style>


---

# まとめ

- 腱鞘炎になると仕事ができないので気をつける
- マウスやキーボード、その他のガジェットで対策はできる
- カーソル移動のデバイスは個人的には以下の評価
  - ■ 精密な動作
    - Trackpad < トラックボール < マウス
  - ■ ドラック & 範囲指定のしやすさ
    - Trackpad < トラックボール < マウス
  - ■ カスタマイズ性
    - マウス < トラックボール < Trackpad
  - ■ 腕の負担の低さ
    - マウス < Trackpad < トラックボール
<style>
a {
  color: #84b9cb;
  @apply font-500;
}

p {
  margin: 1rem !important;
}

div {
  color: #4d4c61;
}

span {
  font-size:0.9rem;
  line-height: 0.5rem !important;
}

strong {
  color: #1f3134;
}

ul {
  padding-left: 1rem;
  margin-top: 0.1rem;
  font-size:1rem;
}

li {
  @apply font-500;
}
</style>


---
layout: center
class: "text-center"
---

<div class="text-2xl font-700 text-enter w-full">
  <div>ご清聴ありがとうございました</div>
</div>

<style>
.main {
  display: flex;
  height: 80%;
  width: 100%;
  justify-content: center;
  align-items: center;
  color: #46AE35;
}
</style>
