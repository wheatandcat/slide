---
theme: ./theme
class: text-center
background:
highlighter: shiki
lineNumbers: false
info: |
  ##  作成中のFlutterアプリの中間発表
drawings:
  persist: false
title: |
   作成中のFlutterアプリの中間発表
colorSchema: dark
fonts:
  sans: Noto Sans Japanese
  serif: Roboto Slab
  mono: Fira Code
---

### 作成中のFlutterアプリの中間発表

<div class="flex justify-center pt-10">
  <img
    class="w-50 pt-2"
    src="/logo.svg"
  />
</div>

<div class="pt-12">
  <span @click="$slidev.nav.next" class="px-2 py-1 rounded cursor-pointer" hover="bg-white bg-opacity-10">
    Press Space for next page <carbon:arrow-right class="inline"/>
  </span>
</div>

<!--
The last comment block of each slide will be treated as slide notes. It will be visible and editable in Presenter Mode along with the slide. [Read more in the docs](https://sli.dev/guide/syntax.html#notes)
-->

---
transition: fade-out 
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

- 📝 飯野陽平（[wheatandcat](https://github.com/wheatandcat))
- 🏢 会社: [合同会社UNICORN](https://www.unicornllc.dev/) 代表社員
- 📚 Blog: https://www.wheatandcat.me/
- 🛠 今までに作ったもの
  - [memoir](https://memoir-lp-mvbeacmwe-wheatandcat.vercel.app/)
  - [OOMAKA](https://oomaka.vercel.app)
  - [MarkyLinky](https://github.com/wheatandcat/MarkyLinky)

<style>
ul {
  padding-left: 1rem;
  margin-top: 0.1rem;
}
li {
  @apply font-500;
  font-size:1.15rem;
}
a {
  color: #84b9cb;
  @apply font-500;
}
</style>


---
transition: fade-out 
layout: image-left
image: /screen_01.png
---

# 最近作っているアプリの紹介

- アプリ名: **Stock Keeper**
- 内容
   - 在庫管理アプリ
   - 家族で共有して使える
   - 家族で同じものを買いすぎないようにする


<style>
ul {
  padding-left: 1rem;
  margin-top: 0.1rem;
}
li {
  @apply font-300;
  font-size:1.15rem;
}
a {
  color: #84b9cb;
  @apply font-300;
}
</style>

---
layout: image-right
image: /screen_02.png
---

# デザイン
 - Figmaで作成
 - 複雑な操作をしないシンプル設計
 - 部屋を登録して、部屋ごとに在庫を管理できる



<style>
ul {
  padding-left: 1rem;
  margin-top: 0.1rem;
}
li {
  @apply font-300;
  font-size:1.15rem;
}
a {
  color: #84b9cb;
  @apply font-300;
}

p {
  color: #fff !important;
  opacity: 1 !important;
}
</style>


---
layout: image-right
image: /screen_03.png
---

# 技術スタック

 - Flutter
 - NestJS
 - Prism
 - TiDB Serverless
 - Cloud Run
 - Firebase 

<style>
ul {
  padding-left: 1rem;
  margin-top: 0.1rem;
}
li {
  @apply font-300;
  font-size:1.15rem;
}
a {
  color: #84b9cb;
  @apply font-300;
}

p {
  color: #fff !important;
  opacity: 1 !important;
}
</style>

---
transition: fade-out 
layout: fact
---

# デモをやる


<style>
ul {
  padding-left: 1rem;
  margin-top: 0.1rem;
}
li {
  @apply font-300;
  font-size:1.15rem;
}
a {
  color: #84b9cb;
  @apply font-300;
}

p {
  color: #fff !important;
  opacity: 1 !important;
}
</style>

---
layout: default
---

# デモの工程

## iOSで起動
 - ログイン
 - アイテム登録
 - [image_picker](https://pub.dev/packages/image_picker)、[image_cropper](https://pub.dev/packages/image_cropper)の紹介
 - VSCodeのデバッグ紹介

## Androidで起動
 - ログイン
 - アイテム登録

## webで起動
 - ログイン

<style>
ul {
  padding-left: 1rem;
  margin-top: 0.1rem;
}
li {
  @apply font-300;
  font-size:1.15rem;
}
a {
  color: #84b9cb;
  @apply font-300;
}

p {
  color: #fff !important;
  opacity: 1 !important;
}
</style>


---
layout: default
---

# まとめ
  - マルチプラットフォームの完成度が、かなり高い
  - 画像アップロードは一部web専用の実装が必要だったが、他は同じコードで実装できている
    - Flutter以外にもマルチプラットフォーム系はあるが、現状Flutterが一番完成度が高い
   - Flutter stable 3.22で**Wasm**がサポートされるので、さらにwebの品質が上がりそう
  - Firebase Authenticationの実装が簡単
    - 以下のコマンド実行で全プラットフォームの初期設定が完了
    - ```bash
      $ flutterfire configure
      ```
    - 詳細は[こちら](https://firebase.google.com/docs/flutter/setup?hl=ja&platform=ios)
    - Google開発なだけあり、Google産サービスとの連携が強い

<style>
ul {
  padding-left: 1rem;
  margin-top: 0.1rem;
}
li {
  @apply font-300;
  font-size:1.15rem;
}
a {
  color: #84b9cb;
  @apply font-300;
}
p {
  color: #fff !important;
  opacity: 1 !important;
}
</style>

---
layout: center
class: "text-center"
---

<div class="text-2xl font-700 text-enter w-full">
  <div>ご清聴ありがとうございました 🎉 </div>
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
