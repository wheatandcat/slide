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
  # Plasmoの紹介
# persist drawings in exports and build
drawings:
  persist: false
title:  Plasmoの紹介
layout: intro
colorSchema: "light"
---

## **Plasmo**の紹介

<div class="flex justify-center">
  <img
    class="w-30 pt-2"
    src="/logo.jpeg"
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
- 🏢 法人設立（[合同会社UNICORN](https://www.unicornllc.dev/) 代表社員）
- 💻 Work: シェアフル株式会社CTO
- 📚 Blog: https://www.wheatandcat.me/
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

## **Plasmo**とは？

<br/>

- ブラウザ拡張機能を作成するためのReactフレームワーク
- **TypeScript & React**で簡単にChrome拡張が作成できる
- 従来のChrome拡張で必要だった設定周りフレームワーク側で抽象化されている

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

## セットアップ

<br/>

以下のコマンド実行でプロジェクトの作成ｇは完了

```bash
$ pnpm create plasmo
```

<br/>
<br/>

 - [Getting Started | Plasmo](https://docs.plasmo.com/framework)


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

## コード

プロジェクトの作成時は以下のようなコードが生成される

```tsx
import { useState } from "react"

function IndexPopup() {
  const [data, setData] = useState("")
  return (
    <div>
      <h2>
        Welcome to your{" "}
        <a href="https://www.plasmo.com" target="_blank">
          Plasmo
        </a>{" "}
        Extension!
      </h2>
      <input onChange={(e) => setData(e.target.value)} value={data} />
      <a href="https://docs.plasmo.com" target="_blank">
        View Docs
      </a>
    </div>
  )
}
export default IndexPopup
```


<style>
a {
  color: #84b9cb;
  @apply font-500;
}

div {
  color: #4d4c61;
}

span {
  font-size:0.25rem;
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

## 簡単なChrome拡張を作成したので紹介

<br/>

<b>■ plasmo-demo</b><br/>
https://github.com/wheatandcat/plasmo-demo


<div class="flex justify-center">
  <img
    class="w-3/4 pt-2"
    src="/screen_01.png"
  />
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

## モチベーション

<br/>

 - 技術系記事をストックする機能が欲しかった
 - ブラウザのブックマークやGoogle Keepだと、見返した時にどこに保存したか忘れるケースが多い
 - 大体のケースは読み終わったら削除してOKだが、既存だと削除が手間なシステムが多い
 - まだ開発中なので、ここから自分好みにカスタマイズしていく予定

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

## デモ

<br/>

 - 以下は動かしながら紹介する
   - コード
     - https://github.com/wheatandcat/plasmo-demo/blob/main/popup.tsx
   - データの保存は[PlasmoのStorage API](https://docs.plasmo.com/framework/storage)を使用
   - デザインは[TailwindCSS](https://docs.plasmo.com/quickstarts/with-tailwindcss)を使用
   - 右クリックのMenuに追加は[Background Service Worker](https://docs.plasmo.com/framework/background-service-worker)を使えば可能
     - [コード](https://github.com/wheatandcat/plasmo-demo/blob/main/background.ts)
   

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
  margin-top: 0.2rem;
}

li {
  @apply font-500;
  margin-top: 0.5rem;
  font-size: 1rem;
}
</style>



---

## まとめ

<br/>

 - かなり簡単にChrome拡張が作れるのでオススメ
 - デバッグツールとか作っても良いかも
 - Chrome拡張特有の部分は抽象化しているので、Reactさえ知っていれば誰でも自作できる


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
