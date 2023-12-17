---
theme: ./theme
class: text-center
background:
highlighter: shiki
lineNumbers: false
info: |
  ## App Routerの紹介
drawings:
  persist: false
title: |
  App Routerの紹介
colorSchema: dark
fonts:
  sans: Noto Sans Japanese
  serif: Roboto Slab
  mono: Fira Code
---

# App Routerの紹介

<div class="flex justify-center pt-10">
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

- 📝 飯野陽平（[wheatandcat](https://github.com/wheatandcat)）
- 🏢 法人設立（[合同会社UNICORN](https://www.unicornllc.dev/) 代表社員）
- 💻 Work: シェアフル株式会社CTO
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
  @apply font-500;
  font-size:1.15rem;
}
a {
  color: #84b9cb;
  @apply font-500;
}
</style>


---
layout: default
---

# App Routerとは？

- Next.js 13.4で追加された新しいルーティング機構
- 従来のNext.jsのルーティングは**Page Router**
- **RSC**（React Server Components）の使用を前提と設計


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
layout: default
---

# RSC（React Server Components） とは？

- Reactでサーバーサイドでレンダリングできるコンポーネントを宣言できる仕組み
- 元々、Reactにはクライアントサイドでレンダリングする**クライアントコンポーネント**しかなかった
- SSRは、**クライアントコンポーネントをサーバーサイドでレンダリングする仕組み**
- RSCを使用することでサーバーサイド固有の機能を実装できる
  - 例えばReact内で直接データベースにアクセスすることなどが可能
- 逆にRSCではクライアントサイド固有の機能は使用できない
  - 例えば、useStateやuseEffectなどのHooksは使用できない
  - 宣言した時点でエラーになる
- RSCで宣言されたコンポーネントはブラウザ側で読み込みbundleされたJavaScriptには含まれないため、読み込むファイルサイズは小さくなる

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
layout: default
---

# App Routerのルーティング基本機構

- 従来のPage Routerのルーティング機構
  ```bash
  src
   └─ pages
      ├─ index.tsx → /
      └─ items
          ├─ [id].tsx → /items/[id]
          └─ [id]
              └─ share.tsx → /items/[id]/share
  ```

- App Routerのルーティング機構
   ```bash
   src
    └─ app
       ├─ page.tsx → /
       └─ items
           └─ [id]
               ├─ page.tsx → /items/[id]
               └─ share
                   └─ page.tsx → /items/[id]/share
   ```

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
layout: default
---

# ルーティング毎に動的にfavicon、OG画像を変更する


- App Routerのルーティング機構だと以下のように設定が可能
  ```bash
  src
  └─ app
      ├─ layout.tsx  → 共通設定
      └─ items
          └─ [id]
              ├─ icon.tsx → 動的faviconを変更
              └─ opengraph-image.tsx　→ 動的OG画像を変更
  ```

 - 以下、書き方の参考
   - [src/app/icon.tsx](https://github.com/wheatandcat/OOMAKA/blob/d92bd22b4e60da42615a69d0044af3f9c96c860c/src/app/schedule/%5Bid%5D/icon.tsx#L1)

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
layout: default
---

# データアクセス & レンダリングの構造①
App Routerはデフォルトは**RSC**でレンダリングされる、以下、コードの例
```tsx {all|12|13-17|18}
export default function Home() {
  return (
    <div className="container">
      <h1 className="text-5xl">
        Sample App
      </h1>
      <CrudShowcase />
    </div>
  );
}

async function CrudShowcase() {
  const session = await getServerAuthSession();
  if (session?.user) {
    const url = await api.url.existsByUserId.query({userId: String(session?.user.id)});
    if (url) redirect(`/schedule/${String(url?.id)}`);
  }
  return <CreateUrl />;
}
```

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
  color: #fff;
  opacity: 1 !important;
}
span {
  font-size: 0.6rem;
  line-height: 0.6rem;
}

</style>



---
layout: default
---

# データアクセス & レンダリングの構造②

```tsx {all|1|3-23}
"use client";

export function CreateUrl() {
  const router = useRouter();
  const createMutation = api.url.create.useMutation({
    onSuccess: (data) => {
      router.push(`/items/${data.id}`);
    },
  });

  const onCreate = useCallback(() => {
    createMutation.mutate();
  }, [createMutation]);

  return (
    <button
      className="button"
      onClick={onCreate}
    >
      新しいデータを作る
    </button>
  );
}
```

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
  color: #fff;
  opacity: 1 !important;
}
span {
  font-size: 0.6rem;
  line-height: 0.6rem;
}

</style>



---
layout: default
---

# データアクセス & レンダリングの構造③
 - **RSC**ではasync/awaitが使用できる
 - RSCではhooksは使用できないのでデータ更新で使用する**useMutation**は**クライアントコンポーネントで実装する必要がある**
 - RSCでデータ取得する場合は、直接データベースにアクセスが可能なので以下のように実装が可能

<br/>

```tsx {all|1-2|4-8}
export default async function Page({ params }: { params: { id: string } }) {
  const session = await getServerAuthSession();

  const url = await api.url.exists.query({ id: params.id });
  if (url === null) {
    // 存在しないURLの場合はトップページに戻す
    redirect("/");
  }

  ...省略

```


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
  color: #fff;
  opacity: 1 !important;
}
span {
  font-size: 0.6rem;
  line-height: 0.6rem;
}

</style>


---
layout: default
---

# 実装してみる
 - PR: [App Routerに変更する](https://github.com/wheatandcat/OOMAKA/pull/21)
 - 以下、デモしながら説明
   - App Routerの移行で以下の処理はシンプルに実装できた例1
     - [旧コード](https://github.com/wheatandcat/OOMAKA/blob/a89c79cc6fb96fab7612a0174b7cbb94eeebf436/src/pages/schedule/%5Bid%5D.tsx#L16-L30)
     - [新コード](https://github.com/wheatandcat/OOMAKA/blob/17f65b5e2e3444d66009cc9871b3ae3c31e923d7/src/app/schedule/%5Bid%5D/page.tsx#L12-L20)
   - App Routerの移行で以下の処理はシンプルに実装できた例2
     - [旧コード](https://github.com/wheatandcat/OOMAKA/blob/a89c79cc6fb96fab7612a0174b7cbb94eeebf436/src/pages/index.tsx#L20-L40)
     - [新コード](https://github.com/wheatandcat/OOMAKA/blob/17f65b5e2e3444d66009cc9871b3ae3c31e923d7/src/app/page.tsx#L32-L38)


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
  color: #fff;
  opacity: 1 !important;
}
span {
  font-size: 0.6rem;
  line-height: 0.6rem;
}

</style>



---
layout: default
---

## まとめ

 - ここは明日書く

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
  color: #fff;
  opacity: 1;
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
