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
  # T3 Stack + Supabaseでアプリ作ってみる
# persist drawings in exports and build
drawings:
  persist: false
title: T3 Stackの紹介
layout: intro
colorSchema: "light"
---

## **T3 Stack** + **Supabase**で

### アプリ作ってみる

<div class="flex justify-center pt-6">
  <img
    class="w-48 pt-2"
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
- 🏢 法人設立（[合同会社 UNICORN](https://www.unicornllc.dev/) 代表社員）
- 💻 Work: シェアフル株式会社 CTO
- 📚 Blog: https://www.wheatandcat.me/
- 🛠 今までに作ったもの
  - [memoir](https://memoir-lp-mvbeacmwe-wheatandcat.vercel.app/)
  - [ペペロミア](https://peperomia.app/)
  - [MarkyLinky](https://github.com/wheatandcat/MarkyLinky)
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

## **T3 Stack**とは？

<br/>

- 最近、話題の Web アプリ開発のアーキテクチャ
- 以下の 3 つの思想に集点を当てて設計された技術スタック
  - simplicity(簡潔さ)
  - modularity(モジュール性)
  - full-stack typesafety(フルスタックの型安全)
- [t3-app](https://create.t3.gg/)としてコマンドラインツールも公開されている
- 採用されている 6 つの技術については紹介

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

## **Next.js**

<br/>

- [Next.js - The React Framework](https://nextjs.org/)
- React をベースとしたフルスタックフロントエンドフレームワーク
- 大規模な Web アプリケーションでは採用されていることが多い

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

## **tRPC**

<br/>

- [tRPC](https://trpc.io/)
- スキーマやコード生成なしで型安全な API のレスポンスを提供することができるライブラリ
- 以前、紹介のスライドを作成したので詳しくは、以下を参照
  - [tRPC の紹介 - Speaker Deck](https://speakerdeck.com/wheatandcat/trpcnoshao-jie)

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

## **Tailwind CSS**

<br/>

- [Tailwind CSS](https://tailwindcss.com/)
- 最近流行りの CSS フレームワーク
- ユーティリティファーストの思想で設計されており、汎用性が高く、自身で css を作成するコストが大幅に軽減される

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

## **TypeScript**

<br/>

- [TypeScript: JavaScript With Syntax For Types.](https://www.typescriptlang.org/)
- JavaScript を拡張して開発された言語
- 型安全を保ちながら開発を行うことができる

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

## **Prisma**

<br/>

- [Prisma | Next-generation ORM for Node.js & TypeScript](https://www.prisma.io/)
- Node.js 製の ORM
- データベースのスキーマ定義を行うことで、型安全なクエリを実行できる
- 以前、紹介のスライドを作成したので詳しくは、以下を参照
  - [Prisma を試してみた - Speaker Deck](https://speakerdeck.com/wheatandcat/prismawoshi-sitemita)

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

## **NextAuth.js**

<br/>

- [NextAuth.js](https://next-auth.js.org/)
- Next.js をベースとした認証ライブラリ
- 各サービスのログインに対応
- Next.js でフロントエンド、サーバーサイドの API の認証を一元管理できる

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

## T3 Stack を使っててサービスを作ってみた

<br/>

- 使用技術
  - T3 Stack
    - ログインは [Discoed](https://discord.com/)で実装
  - [Supabase](https://supabase.io/)
    - 以前、紹介のスライドを作成したので詳しくは、以下を参照
      - [Supabase の紹介 - Speaker Deck](https://speakerdeck.com/wheatandcat/supabasenoshao-jie)
  - [vercel](https://vercel.com/)
  - [Figma](https://www.figma.com/file/9YviKZnCT9UlmLNO6KjdoF/OOMAKA?type=design&node-id=1-2&mode=design)
- リポジトリ
  - https://github.com/wheatandcat/OOMAKA

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

## 作ったサービス

<br/>

<div class="flex justify-center">
  <img
    class="w-2/5 pt-2  border-1 border-black border-dotted border-opacity-20"
    src="/screen_001.png"
  />
</div>

- **サービス名**: OOMAKA
- **URL**: https://oomaka.vercel.app
- **概要**: 大まかに未来の予定を可視化するサービス

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

## 実装の紹介

<br/>

- [デモURL](https://oomaka.vercel.app/)
- ※以下、デモしながら紹介
- DB設計はPrismaで[prisma/schema.prisma](https://github.com/wheatandcat/OOMAKA/blob/06a462c7a54007e1294d0f0387f5862090343038/prisma/schema.prisma#L24)の通りに定義
- Next.jsでAPI実装は[API Routes](https://nextjs-ja-translation-docs.vercel.app/docs/api-routes/introduction)を使用
- tRPC + Prismaは[src/server/api/routers/url.ts](https://github.com/wheatandcat/OOMAKA/blob/86e884416e655b3c8438588491b60d79e5849d3b/src/server/api/routers/url.ts#L1)のように実装
- フロントエンド側の実装は以下の通り
  - 読み込みは[src/pages/index.tsx](https://github.com/wheatandcat/OOMAKA/blob/ec72b9ac86e99e80ff3ab7a9e7ffafbf9fb4c1b0/src/pages/index.tsx#L14-L16)のようにして取得
  - 書き込みは[src/pages/index.tsx](https://github.com/wheatandcat/OOMAKA/blob/ec72b9ac86e99e80ff3ab7a9e7ffafbf9fb4c1b0/src/pages/index.tsx#L24-L32)のようにして取得
- ログインは[src/pages/index.tsx](https://github.com/wheatandcat/OOMAKA/blob/ec72b9ac86e99e80ff3ab7a9e7ffafbf9fb4c1b0/src/pages/index.tsx#L11)で、サクッと実装できる


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

## まとめ

<br/>

- T3 Stack の開発体験はとても良い
- 今後の Web 開発のスタンダードになる可能性が高い
- データ通信の簡単な部分は tRPC と Prisma で作成して、複雑な部分は gRPC でマイクロサービスに繋いで開発すると、かなり開発効率の高いプロダクトにできそう

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
