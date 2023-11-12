---
theme: ./theme
class: text-center
background:
highlighter: shiki
lineNumbers: false
info: |
  ## T3 Stack（応用編: Next Auth & SSRの実装紹介）
drawings:
  persist: false
title: |
  T3 Stack（応用編: Next Auth & SSRの実装紹介）
colorSchema: dark
fonts:
  sans: Noto Sans Japanese
  serif: Roboto Slab
  mono: Fira Code
---

# T3 Stack
### 応用編: Next Auth & SSRの実装紹介

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

# T3 Stackとは？

- 最近、話題の Web アプリ開発のアーキテクチャ
- 以下の 3 つの思想に集点を当てて設計された技術スタック
  - simplicity(簡潔さ)
  - modularity(モジュール性)
  - full-stack typesafety(フルスタックの型安全)
- [t3-app](https://create.t3.gg/)としてコマンドラインツールも公開されている
- 全体の紹介は以前スライドを作成したので、そちらを参照
  - [T3 Stack + Supabaseでアプリを作ってみる - Speaker Deck](https://speakerdeck.com/wheatandcat/t3-stack-plus-supabasedeapuriwozuo-tutemiru)
- このスライドでは、T3 Stackの応用編として、**Next Auth**と**SSR対応**を紹介 

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

# Next Authとは？

 - Next.jsアプリケーション専用に設計されたオープンソースの認証ライブラリ
 - SSRや、React Server Components等のサーバーサイドでも認証が可能
 - 様々な認証プロバイダーをサポート（Google、Facebookなど）
 - 簡単な設定で認証が実装可能

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

# Next Authで認証を実装

各プロバイダーの設定は以下のように行う

```ts {all|3-6|7-10|all}
export const authOptions: NextAuthOptions = {
  providers: [
    DiscordProvider({
      clientId: env.DISCORD_CLIENT_ID,
      clientSecret: env.DISCORD_CLIENT_SECRET,
    }),
    AppleProvider({
      clientId: env.APPLE_ID,
      clientSecret: env.APPLE_SECRET,
    }),
    GoogleProvider({
      clientId: env.GOOGLE_CLIENT_ID,
      clientSecret: env.GOOGLE_CLIENT_SECRET,
    }),
  ],
```

 - [Google | NextAuth.js](https://next-auth.js.org/providers/google)

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
transition: slide-up
level: 2
---

# ログイン画面の実装

プロバイダーの設定が完了したら、**signIn**のメソッドをコールするだけで以下の画面

```ts {all}
import { signIn, signOut, useSession } from "next-auth/react";

<button onClick={() => signIn("credentials", {callbackUrl: "/",})}>
  ログイン
</button>
```

<div class="flex justify-center pt-3">
  <img
    class="w-80 pt-2"
    src="/screen001.png"
  />
</div>


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

# ログイン画面のカスタマイズ

ログイン画面をカスタマイズしたい場合は以下を追加することで可能

```ts {all}
export const authOptions: NextAuthOptions = {
  pages: {
    signIn: "/auth/signin",
    error: "/auth/signin",
  },
```

<div class="flex justify-center pt-3">
  <img
    class="w-80 pt-2"
    src="/screen002.png"
  />
</div>


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
layout: default
---

# 認証実装①（クライアントサイドで取得）

認証したユーザーの値は以下で取得可能

```ts {all|1,4|6-8|12-15|all}
import { signIn } from "next-auth/react";

function Home() {
  const { data: session } = useSession();

  if (!session) {
    return (<div>ログイン前です</div>)
  }

  return (
    <div>
      <div>ログイン後です</div>
      <div>{session.user.id}</div>
      <div>{session.user.name}</div>
      <div>{session.user.email}</div>
    </div>
  )
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
  opacity: 1;
}
</style>

---
layout: default
---

# 認証実装②（SSRで認証）

SSRで認証したい場合は以下のように実装

```ts {all|5-10|13|all}
import { signIn } from "next-auth/react";
import { type GetServerSideProps } from "next";
import { getServerAuthSession } from "~/server/auth";

export const getServerSideProps: GetServerSideProps = async (ctx) => {
  const session = await getServerAuthSession(ctx);
  return {
    props: { session },
  };
};

function Home() {
  const { data: session } = useSession();
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
  opacity: 1;
}
</style>


---
layout: default
---

# 認証実装③（RSCで認証）

RSCで認証したい場合は以下のように実装<br/>
現状はこれが最速の認証方法

```ts {all|4-5|all}
import { getServerSession } from "next-auth/next"
import { authOptions } from "~/server/auth";

export default async function Home() {
  const session = await getServerSession(authOptions)
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
  opacity: 1;
}
</style>


---
layout: default
---

# tRPCでSSRを実装①

T3 StackではtRPCでデータ取得を行っている<br/>
SSRに対応するには、以下のoptionを**true**にするだけでOK 👌

```ts {all|9}
import { createTRPCNext } from "@trpc/next";

export const api = createTRPCNext<AppRouter>({
  /**
   * Whether tRPC should await queries when server rendering pages.
   *
   * @see https://trpc.io/docs/nextjs#ssr-boolean-default-false
   */
  ssr: true,
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
  opacity: 1;
}
</style>

---
layout: default
---

# tRPCでSSRを実装②

**ssr:true**にするとtRPCでアクセスしている箇所をサーバーサイドで**prefetch**する挙動になる<br/>以下のようなコードを実行した場合、クライアントサイドではキャッシュから取得するの動作になる

```ts {all|5|all}
function Schedule() {
  const router = useRouter();
  const { id } = router.query;

  const schedules = api.schedule.fetch.useQuery({ urlId: String(id) });
```

- [Server-Side Rendering | tRPC](https://trpc.io/docs/client/nextjs/ssr)

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
layout: default
---

# 補足: スライドで参照している開発物の紹介

 - Repository
   - [OOMAKA](https://github.com/wheatandcat/OOMAKA)
 - サービスURL
   - [OOMAKA | 年間スケジュール、まとめるなら](https://oomaka.vercel.app/)
 - SSRしている画面を軽くDEMO
   

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

## まとめ

 - T3 Stackを使うとSSR周りは、かなり楽
 - **getServerSideProps**でゴニョゴニョする必要がなくなって開発が捗る
 - Next Authは現状はNext.js専用だが、今後のロードマップで名前をAuthに変更して別フレームワークでも使用可能になる予定

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
