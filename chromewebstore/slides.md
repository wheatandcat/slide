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
  # 1人でChrome拡張を開発してChrome Web Storeに公開した話
# persist drawings in exports and build
drawings:
  persist: false
title: 1人でChrome拡張を開発してChrome Web Storeに公開した話
layout: intro
colorSchema: "light"
---

<div class="pb-10 font-bold text-gray-700">1人でChrome拡張を開発してChrome Web Storeに公開した話</div>


<div class="flex justify-center">
  <img
    class="w-60 pt-2"
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
- 🏢 [合同会社UNICORN](https://www.unicornllc.dev/) 代表社員
- 💻 Client Work: シェアフル株式会社CTO
- 📚 Blog: https://www.wheatandcat.me/
- 🛠 今までに作ったもの
  - [memoir](https://memoir-lp-mvbeacmwe-wheatandcat.vercel.app/)
  - [ペペロミア](https://peperomia.app/)
  - [MarkyLinky](https://github.com/wheatandcat/MarkyLinky)


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

## 概要

<br/>

 - 1人でChrome拡張を開発してChrome Web Storeに公開したので、公開に必要な手順を紹介
 - ◆ このスライドで紹介する内容
   - 開発したChrome拡張の紹介
   - Chrome Web Storeに公開する手順
   - 1人でアプリを公開するためのTips


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

## 開発したChrome拡張の紹介

<br/>


<div class="flex justify-around">
  <img
    class="w-60 border-2 border-black border-dotted border-opacity-20"
    src="/screen03.png"
  />
  <img
    class="w-60  border-2 border-black border-dotted border-opacity-20"
    src="/screen01.png"
  />
  <img
    class="w-60 border-2 border-black border-dotted border-opacity-20"
    src="/screen02.png"
  />
</div>

 - ■ GitHub
   - https://github.com/wheatandcat/MarkyLinky/
 - ■ Chrome Web Store
   - [MarkyLinky - Chrome ウェブストア](https://chrome.google.com/webstore/detail/markylinky/kjjjfmbnaamaogjpjdgeiffgjabbpmfp?hl=ja)


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

## 使用技術

<br/>

 - 開発フレームワーク
   - [Plasmo](https://docs.plasmo.com/)
 - CSS
   - [Tailwind CSS](https://tailwindcss.com/)
 - 認証/データベース
   - [supabase](https://supabase.com/)

<style>
a {
  color: #84b9cb;
  @apply font-500;
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

<div class="flex justify-center items-center h-full">
  <div class="text-3xl font-bold">デモで、アプリを紹介</div>
</div>

<style>
a {
  color: #84b9cb;
  @apply font-500;
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

## Chrome Web Storeに公開する手順

<br/>

 - ◆ 必要なもの
   - **GCPプロジェクト**
     - Store公開にOAuthのクライアントIDを取得
     - **Chrome Web Store API**を有効にする
   - **Chrome Web Store Developerの登録**
     - 初回のみ$5の登録料金がかかる

<style>
a {
  color: #84b9cb;
  @apply font-500;
}

div {
  color: #4d4c61;
}

span {
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

## Chrome Web Storeの審査①

<br/>

 - 以下の情報が必須
   - ストアのサムネイル画像
   - ストアのアイコン画像
   - アプリの説明
   - アプリの権限周りの説明
   - ※実際のStore画面を見せて解説する

<style>
a {
  color: #84b9cb;
  @apply font-500;
}

div {
  color: #4d4c61;
}

span {
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

## Chrome Web Storeの審査②

<br/>

 - 審査の期間
   - アプリの権限によって変わるが、**4〜5日程度**
     - ※結構長いので注意 🐢
 - 初回公開までの審査で落とされた部分
   - 権限周りは厳重にチェックされる
     - アプリで使用していない権限がある場合は落とされる
     - 参考
       - https://github.com/wheatandcat/MarkyLinky/issues/13
     - manifest.jsonの設定を見直せば通る

<style>
a {
  color: #84b9cb;
  @apply font-500;
}

div {
  color: #4d4c61;
}

span {
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

## 1人でStore公開するのはTips

<br/>

 - 開発以外の部分で詰まった箇所は以下の3つ
   - アプリ名の決定
   - アイコン作成
   - ストア文言作成

<style>
a {
  color: #84b9cb;
  @apply font-500;
}

div {
  color: #4d4c61;
}

span {
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
clicks: 1
---

## アプリ名の決定

<br/>

 - ChatGPTでアプリ名を決めてみた
 - プロンプトは以下の通りで出力

<img v-click="0" v-if="$slidev.nav.clicks === 0"
  class="w-100"
  src="/name001.png"
/>

<img v-click="1" v-if="$slidev.nav.clicks === 1"
  class="w-100"
  src="/name002.png"
/>



<style>
a {
  color: #84b9cb;
  @apply font-500;
}

div {
  color: #4d4c61;
}

span {
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

## アイコン作成

<br/>

 - 今回は[Wixロゴメーカー](https://ja.wix.com/logo/maker)
 - ロゴとアイコンを自動生成してくれるサービス
 - アプリ名とキーワードを入力するだけで簡単に作成できる
  - 以下で軽くデモ
    - https://manage.wix.com/logo/maker/esh/welcome
 - ロゴだけだったら、**2,100円で商業利用も可能**


<style>
a {
  color: #84b9cb;
  @apply font-500;
}

div {
  color: #4d4c61;
}

span {
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
clicks: 1
---

## ストア文言作成

<br/>

 - ここでもChatGPTを利用して作成
 - プロンプトは以下の通りで出力
   - 正直こういう文章を書く才能が全くないので助かった 🥳

<img v-click="0" v-if="$slidev.nav.clicks === 0"
  class="w-100"
  src="/store001.png"
/>

<img v-click="1" v-if="$slidev.nav.clicks === 1"
  class="w-100"
  src="/store002.png"
/>


<style>
a {
  color: #84b9cb;
  @apply font-500;
}

div {
  color: #4d4c61;
}

span {
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

## まとめ

<br/>

 - 1人でStore公開すると開発以外の部分で詰まることが多かったが、今回はAI系で突破してみた
 - サクッと開発して公開したい時には十分通用する手だなと思った
 - Chrome拡張の開発は手軽で楽しいので、結構おすすめ


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
