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
  ## TauriでカスタマイズしたTODOアプリを作ってみる
# persist drawings in exports and build
drawings:
  persist: false
title:  TauriでカスタマイズしたTODOアプリを作ってみる
layout: intro
colorSchema: "light"
---

##  **Tauri**でカスタマイズしたTODOアプリを作ってみる

<div class="flex justify-center">
  <img
    class="w-30 pt-2"
    src="/logo.png"
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

# **Tauri**とは

<br/>

- **Tauri**は**Rust**で作成されたクロスプラットフォームでデスクトップアプリが作成できるフレームワーク
- デスクトップアプリのネイティブ部分のコードは**Rust**、フロントエンドは**Webの技術**を使用できる
  - なのでフロントエンドに関しては以下を使用できる
    - HTML
    - React
    - Next.js
    - Svelte
- 開発の領域的には、**Electron**と同じ


<br/>

- [Tauri](https://tauri.app/)
- [Rust](https://www.rust-lang.org/ja/)


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
  font-size:1rem;
}
</style>


---

# **Electron**との比較

  - 違いについては以下を参照
    - [Tauri 1.0が正式リリース！概要や特徴、Electronとの違いを解説 | アンドエンジニア](https://and-engineer.com/articles/YvkkZxAAACIAiyfE)
  - 主な違い以下の部分
    - Electronは、**Chromium**をそのままバンドルしているがWebViewエンジンの[wry](https://github.com/tauri-apps/wry)を使用している
    - Rustで実装されており、バンドルサイズ、消費CPU、セキュリティ共に改善されている

<br/>
<br/>

- [Electron](https://www.electronjs.org/ja/docs/latest)


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
  font-size:1rem;
}
</style>

---
layout: image-right
---

# TODOアプリを作ってみた

<div class="absolute w-full">
  <div class="absolute right-20">
  <img
    class="w-120 pt-2"
    src="/screen_01.png"
  />
  </div>
</div>


<br/>
<br/>
<br/>

 - **Tauri**を使用してTODOアプリを作ってみた。
 - GitHub
   - https://github.com/wheatandcat/todo
 - 使用技術
   - [Tauri](https://tauri.app/)
   - [React](https://ja.reactjs.org/)
   - [markdown-to-jsx](https://probablyup.com/markdown-to-jsx/)
   - [Tailwind CSS](https://tailwindcss.com/)




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
  font-size:1rem;
}
</style>


---

# モチベーション

<br/>

- 仕事のTODOリストは今までslackのDMに書いて運用していた
  - 雑な運用でリストで書き出して、タスクが終わったら「✔」をつけるのみを運用
    - （実際にslackを表示）
  - 他のTODOアプリも試したが無駄にリッチなアプリが多くて続かなかった
  - ブラウザだと、他の作業で間違って消したりするのでデスクトップアプリで作りたかった
  - 仕事のTODOだとセンシティブな内容が多かったので、サーバー通信は避けたい
 - なので、自分用にカスタマイズしたTODOアプリを作ってみた

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


</style>

---

#  **Tauri**での開発①

<br/>
以下でブラウザでローカル環境を起動

```bash
$ yarn dev
```

これだとブラウザで起動するので、ブラウザのDevToolも活用できる。


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
  font-size:1rem;
}
</style>

---

#  **Tauri**での開発②

<br/>
以下でデスクトップアプリでローカル環境を起動

```bash
$ yarn tauri dev
```

これだとデスクトップアプリの状態で起動するので、ネイティブの機能をデバッグする場合は、<br/>こちらで起動。<br/>
<br/>
ホットリロードも有効なので、快適に開発できる。


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
  font-size:1rem;
}
</style>

---

#  **Tauri**での開発③

<br/>
以下でデスクトップアプリをビルド

```bash
$ yarn tauri build
```

デフォルトだとhostのデバイの環境で起動できるアプリにビルド。
<br/>

以下のオプションで各バイナリに変換可能。
 - [binary options](https://tauri.app/v1/guides/building/macos#binary-targets)

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
  font-size:1rem;
}
</style>

---

# frontendの開発

<br/>

- frontendは**React**で作成
  - [コード](https://github.com/wheatandcat/todo/blob/187301f71db9c572382ab3b73bb6a0bf80d1eb68/src/App.tsx#L1)
- Markdownの表示は[markdown-to-jsx](https://probablyup.com/markdown-to-jsx/)を使用
  - [コード](https://github.com/wheatandcat/todo/blob/187301f71db9c572382ab3b73bb6a0bf80d1eb68/src/components/organisms/Editor.tsx#L1)
- Markdownのparseは[remark-parse](https://www.npmjs.com/package/remark-parse)を使用
  - checkbox部分のパースする自前で作成
  - [コード](https://github.com/wheatandcat/todo/blob/187301f71db9c572382ab3b73bb6a0bf80d1eb68/src/lib/task.ts#L11-L52)


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
  font-size:1rem;
}
</style>

---

# ネイティブ機能の開発

<br/>

- アプリのmenuは以下で作成
  - [コード](https://github.com/wheatandcat/todo/blob/c671fa2804b11c748a73a0e514a33918d7a4221e/src-tauri/src/main.rs#L15-L50)
  - 詳細は、[こちら](https://tauri.app/v1/guides/features/menu/)
- menuからfrontend側の通信は、以下のように作成
  - ネイティブから送信
    - [コード](https://github.com/wheatandcat/todo/blob/c671fa2804b11c748a73a0e514a33918d7a4221e/src-tauri/src/main.rs#L38-L39)
  - frontendで受け取り
    - [コード](https://github.com/wheatandcat/todo/blob/187301f71db9c572382ab3b73bb6a0bf80d1eb68/src/App.tsx#L47-L51) 
    - frontend側から、Tauri APIを使用してネイティブの機能も活用可能
      - [@tauri-apps/api | Tauri Apps](https://tauri.app/v1/api/js/)

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
  font-size:1rem;
}
</style>

---

# まとめ

<br/>

- [Tauri](https://tauri.app/)での開発は快適
- React経験者なら、**ほぼ学習コスト無しで作れる**
- ネイティブ機能の部分が[Rust](https://www.rust-lang.org/ja/)なので書きやすい
  - ビルドが通れば、ほぼOKな感じの安心感がある
- ちゃんと開発できたらApple/Windowsストアで公開する予定

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
