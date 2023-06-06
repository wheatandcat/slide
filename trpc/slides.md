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
  # tRPCの紹介
# persist drawings in exports and build
drawings:
  persist: false
title:  tRPCの紹介
layout: intro
colorSchema: "light"
---

## **tRPC**の紹介

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
- 🏢 法人設立（[合同会社UNICORN](https://www.unicornllc.dev/) 代表社員）
- 💻 Work: シェアフル株式会社CTO
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

## **tRPC**とは？

<br/>

- スキーマやコード生成なしで型安全なAPIの連携が行えるPRCフレームワーク
- 比較対象としては、[GraphQL](https://graphql.org/)や[OpenAPI](https://swagger.io/specification/)などの技術に該当
- TypeScriptに特化しており、非常にシンプルに実装できる
- BFFとして利用されることも多い


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

## そもそも**RPC**とは？

<br/>

- RPC ( Remote Procedure Call ) とは、ネットワークで繋がっている別のコンピュータのプログラムを実行できるようにする技術
- クライアント側からサーバー側への疎通を行う際に、具体的な通信手段やプロトコルを意識することなく、関数の呼び出しを行うことがでやり取りが行える仕組み
- Googleが開発したRPCのプロトコルなので、**gRPC**という命名になっている
- **tRPC**のtはTypeScriptを表している


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

## 学ぶモチベーション

<br/>

 - OpenAPIやGraphQLだとスキーマ定義が必須でコード以外の実装が入りファットになりがち
   - またフロントエンド側を型安全にするためには、さらに別途でコード生成の対応が必要
 - 気軽にかつ型安全を保ちながらAPIを実装したい
 - なので、tRPCを使ってみた

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

## サーバー側の実装

<br/>


```typescript {all|6-10|18|all}
import { createHTTPServer } from "@trpc/server/adapters/standalone";
import { initTRPC } from "@trpc/server"

const t = initTRPC.create();

const appRouter = t.router({
  helloWorld: t.procedure.query(() => {
    return "Hello World";
  }),
});

export type AppRouter = typeof appRouter;

const server = createHTTPServer({
  router: appRouter,
});

server.listen(8000);
```

 - [参考:quickstart](https://trpc.io/docs/quickstart)

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

## クライアント側の実装（スクリプト）

<br/>

```typescript
import { createTRPCProxyClient, httpBatchLink } from "@trpc/client";
import type { AppRouter } from "./server";

const trpc = createTRPCProxyClient<AppRouter>({
  links: [
    httpBatchLink({
      url: "http://localhost:3000",
    }),
  ],
});

trpc.helloWorld.query().then((res) => {
  // output "Hello World"
  console.log(res);
});

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

## クライアント側の実装（スクリプト）

<br/>

 - コードでは以下のように補完が表示される

 <br/>

<img src="/screen_01.png" width="600"/>


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

## クライアント側の実装（React)

<br/>

 - 公式でHooksが提供されているので使用して実装
   - https://trpc.io/docs/reactjs/setup


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

## クライアント側の実装（React)

■ containers/Trpc.tsx
```tsx
import { useState } from "react";
import { QueryClient, QueryClientProvider } from "@tanstack/react-query";
import { httpBatchLink } from "@trpc/client";
import { trpc } from "../utils/trpc";

type Props = {
  children: React.ReactNode;
};

function Trpc(props: Props) {
  const [queryClient] = useState(() => new QueryClient());
  const [trpcClient] = useState(() =>
    trpc.createClient({
      links: [
        httpBatchLink({
          url: "http://localhost:8080",
        }),
      ],
    })
  );

  return (
    <trpc.Provider client={trpcClient} queryClient={queryClient}>
      <QueryClientProvider client={queryClient}>
        {props.children}
      </QueryClientProvider>
    </trpc.Provider>
  );
}

export default Trpc;

```

<style>
a {
  color: #84b9cb;
  @apply font-500;
}

p {
  margin-bottom: 0 !important;
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

pre {
  line-height: 0.9rem !important;
}

li {
  @apply font-500;
  margin-top: 0.25rem;
}
</style>

---


## クライアント側の実装（React)

■ Page.tsx
```tsx
import { trpc } from "./utils/trpc";

export default function IndexPage() {
  const userQuery = trpc.helloWorld.useQuery();

  return <div>{userQuery.data}</div>;
}
```

<style>
a {
  color: #84b9cb;
  @apply font-500;
}

p {
  margin-bottom: 0 !important;
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

## デモ: React + tRPC + Prismaで実装

<br/>

 - ■ GitHub
   - https://github.com/wheatandcat/tRPC-demo/tree/main/trpc-react-prisma
 - デモを見せながらコードを解説
 - PrismaでDBの定義を行う
   - [server/prisma/schema.prisma](https://github.com/wheatandcat/tRPC-demo/blob/1b650957435519964f67a7340c019d57c94522e4/trpc-react-prisma/server/prisma/schema.prisma#L5)
 - tRPCとPrismaの連携
   - [server/src/router.ts](https://github.com/wheatandcat/tRPC-demo/blob/1b650957435519964f67a7340c019d57c94522e4/trpc-react-prisma/server/src/router.ts#L14-L34)
 - Reactとの連携
   - [client/src/Page.tsx](https://github.com/wheatandcat/tRPC-demo/blob/1b650957435519964f67a7340c019d57c94522e4/trpc-react-prisma/client/src/Page.tsx)

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

## 補足: Deno + tRPCを試す

<br/>

 - ■ GitHub
    - https://github.com/wheatandcat/deno-trpc-demo
 - モチベーション
   - 何だかんだでTypeScriptをデプロイするのが面倒だったので、Denoで行けたら1つで全て済むと思って試してみた
 - 結果
   - tRPCの実装はできるけど、Denoで実装したファイルをimportできるのはDenoのみなので、結果フロントエンドもDenoで実装する必要がある
   - こうなってくると旨味が薄れるので、まだ実用段階ではなかったなという感想  

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

## 補足: 手軽にtRPCを試すなら**Create T3 App**がおすすめ

<br/>

 - **T3 Stack**のdemoアプリを簡単に作成できる
   - [フロントエンド界隈で新しく提唱されているT3 Stackについて調べてみた](https://zenn.dev/mikinovation/articles/20220911-t3-stack)
   - 実行方法は以下を参照
     - [Introduction • Create T3 App](https://create.t3.gg/en/introduction)


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

 - コードジェネートして型安全をする方法に慣れきっていたが、tRPCはコードジェネートしなくても型安全が実現できるので手軽感がかなりある
 - TypeScript周りのツールも大分充実してきて書きやすいので、tRPCを使っていくのも全然有り
 - BFF構成なら、GraphQLより筋が良さそう


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
