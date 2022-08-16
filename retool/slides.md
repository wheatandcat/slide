---
# try also 'default' to start simple
theme: default
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: https://source.unsplash.com/collection/94734566/1920x1080
# apply any windi css classes to the current slide
class: 'text-center'
# https://sli.dev/custom/highlighters.html
highlighter: shiki
# show line numbers in code blocks
lineNumbers: false
# some information about the slides, markdown enabled
info: |
  ## zxとRetoolでコード健全性の可視化のダッシュボードを作成する
# persist drawings in exports and build
drawings:
  persist: false
title: zxとRetoolでコード健全性の可視化のダッシュボードを作成する
layout: intro
colorSchema: 'light'
---

## **Retool**と**zx**でコード健全性の可視化のダッシュボードを作成する

<div class="flex justify-center">
  <br/>
  <br/>
  <br/>
  <img
    class="w-120 pt-15"
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
a {
  color: #84b9cb;
  @apply font-500;
}

div {
  color: #4d4c61;
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
  font-size:1rem;
}
</style>

---

# インスパイヤ元の記事紹介

<br/>

 - [zx + Datadog + GitHub Actions でフロントエンドのコードベースの健全性を可視化する](https://zenn.dev/ryo_kawamata/articles/create-frontend-dashboard)
 - こちらの記事で紹介していた内容がインスパイヤ元の記事
 - **Datadog**は、有料サービスなので個人開発では、ちょっと・・・という人向けに、別の方法を紹介

<style>
a {
  color: #84b9cb;
  @apply font-500;
}

div {
  color: #4d4c61;
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
  font-size:1rem;
}
</style>


---

# zxとは？

 - リポジトリ: [zx](https://github.com/google/zx)
 - Google製のJavaScript文法でShellScriptが実行できる
 - mjsの拡張子で、そのまま実行もできるし、JavaScript内にimportしてコード内で使用することも可能

.mjsで使用する場合は、以下みたいな感じで使用可能。

```js
#!/usr/bin/env zx

await $`cat package.json | grep name`

let branch = await $`git branch --show-current`
await $`dep deploy --branch=${branch}`

await Promise.all([
  $`sleep 1; echo 1`,
  $`sleep 2; echo 2`,
  $`sleep 3; echo 3`,
])

let name = 'foo bar'
await $`mkdir /tmp/${name}`
```

<style>
a {
  color: #84b9cb;
  @apply font-500;
}

div {
  color: #4d4c61;
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
  font-size:1rem;
}
</style>


---

# Retoolとは？①

 - サービス: [Retool](https://retool.com/)
 - ローコード開発ツールで、あらゆるデータベースを元にグラフ、チャート、検索フォーム、データ入力などのUIを作成できるサービス
 - 個人の場合では無料で使用できる
   - [Pricing](https://retool.com/pricing/)
 - 一部jsもサポートしているので、柔軟性も高い  

<style>
a {
  color: #84b9cb;
  @apply font-500;
}

div {
  color: #4d4c61;
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
  font-size:1rem;
}
</style>

---

# Retoolとは？②

 - こんな感じで使用できる（Demo）

<div class="flex justify-center items-center">
<img
  class="w-120 mt-16 border-2"
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

strong {
  color: #1f3134;
}

ul {
  padding-left: 1rem;
  margin-top: 0.1rem;
}
li {
  @apply font-500;
  font-size:1rem;
}
</style>

---

# 今回の実装の概要

 - 前提
   - 無料で利用できる
 - 対象
   - フロントエンドのコードで実装
 - 使用ツール & サービス
   - [TypeScript](https://www.typescriptlang.org/)
   - [zx](https://github.com/google/zx)
   - [Firestore](https://firebase.google.com/products/firestore)
   - [GitHub Actions](https://docs.github.com/ja/actions)
   - [Retool](https://retool.com/)

<style>
a {
  color: #84b9cb;
  @apply font-500;
}

div {
  color: #4d4c61;
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
  font-size:1rem;
}
</style>


---

# 実装してみた①

<br/>

 - PR
   - ①. https://github.com/wheatandcat/memoir/pull/239
   - ②. https://github.com/wheatandcat/memoir/pull/241
 - 実装の紹介（Demo）
   - 基本は以下の記事の通りに実装
     - https://zenn.dev/ryo_kawamata/articles/create-frontend-dashboard
   - **zx**の使い方を説明  
   - [Jest](https://jestjs.io/ja/)からカバレッジを取得する方法
     - [対象コード](https://github.com/wheatandcat/memoir/blob/5bf012849ccf8fce67d944c21c0858ab0378938d/scripts/send-metrics/coverage.ts#L6-L15)
     - Jestのカバレッジレポート確認
   - [Jest](https://jestjs.io/ja/)からテストの実行時間とテスト数を取得する方法
     - [対象コード](https://github.com/wheatandcat/memoir/blob/40a961f2f26da1e53e4f06aff802a5f1c112125a/scripts/send-metrics/jestResult.ts#L10-L27)
     - テスト結果をJSON形式で取得するオプションを使用

<style>
a {
  color: #84b9cb;
  @apply font-500;
}

div {
  color: #4d4c61;
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
  font-size:1rem;
}
</style>

---

# 実装してみた②

   - Firestoreへのデータ保存の方法
     - [対象コード](https://github.com/wheatandcat/memoir/blob/40a961f2f26da1e53e4f06aff802a5f1c112125a/scripts/send-metrics/client.ts#L7-L24)
   - Github Actionsで定期実行
     - [対象コード](https://github.com/wheatandcat/memoir/blob/40a961f2f26da1e53e4f06aff802a5f1c112125a/.github/workflows/metrics.yml#L2-L6)
   - あとは、保存しているデータを元に**Retool**でダッシュボードを作成
     - [ダッシュボード](https://jurassic.retool.com/embedded/public/ca1843e7-ce2b-41ad-92c1-1ca7ff8cd944)
   - Retoolでのダッシュボード作成のDemo 

<style>
a {
  color: #84b9cb;
  @apply font-500;
}

div {
  color: #4d4c61;
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
  font-size:1rem;
}
</style>

---

# まとめ

<br/>

 - 複雑なShellScriptを書くより、素直に**zx**を使ったほうがスッキリしたコードが書ける
 - **Retool**は、汎用的に使えるローコード開発ツールなので、積極的に使っていきたい
 - Retoolはサポートが、かなり充実している散らばっている情報をまとめるのにも、役立ちそう
   - https://retool.com/integrations


<style>
a {
  color: #84b9cb;
  @apply font-500;
}

div {
  color: #4d4c61;
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
  font-size:1rem;
}
</style>

---
layout: center
class: "text-center"
---

<div class="text-2xl font-700 text-enter w-full">
  <div>🎉 ご清聴ありがとうございました 🎉</div>
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


