---
theme: seriph
background:
class: text-center
highlighter: shiki
lineNumbers: false
info: |
  ## Supabaseの紹介
  Learn more at [https://github.com/wheatandcat/slide)
drawings:
  persist: false
transition: slide-left
title: Supabaseの紹介
fonts:
  # basically the text
  sans: 'Robot'
  # use with `font-serif` css class from windicss
  serif: 'Noto Sans Japanese'
  # for code blocks, inline code, etc.
  mono: 'Fira Code'
---

# Supabaseの紹介

<div class="flex justify-center pt-10">
  <img
    class="w-60 pt-2"
    src="/logo.png"
  />
</div>

<div class="pt-12">
  <span @click="$slidev.nav.next" class="px-2 py-1 rounded cursor-pointer" hover="bg-white bg-opacity-10">
    Press Space for next page <carbon:arrow-right class="inline"/>
  </span>
</div>

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

# Supabaseとは？

 - Firebase代替として注目を集めているサービス
 - 現在は以下の機能を提供している
   - Database
   - Authentication
   - Storage
   - Edge Functions

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

# Firebaseとの違い

 - 完全オープンソース
 - データベースはPostgreSQLを使用
 - コンソール画面が非常にモダン
 - 機能数はFirebaseの方が多い

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
transition: slide-up
level: 2
---

# Authentication

 - 認証周りは以下のようなサービスと連携して認証が可能
   - ※ダッシューボードを見せながら説明
   - [リンク](https://supabase.com/docs/guides/auth)
 - 設定はシンプルで使いたいサービスを選択して有効にするだけでOK 👌

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

# コード

以下のようなコードで認証は実装可能[^1]

```ts {all|1,5|14|all}
  const handleOAuthLogin = async (provider: Provider, scopes = "email") => {
    await supabase.auth.signInWithOAuth({
      provider,
      options: {
        scopes,
        redirectTo: location.href
      }
    })
  }

  略）

  // ログイン後は以下から認証情報を取得できる
  const { data, error } = await supabase.auth.getSession()
```

[^1]: [Learn More](https://supabase.com/docs/guides/auth)

<style>
.footnotes-sep {
  @apply mt-20 opacity-10;
}
.footnotes {
  @apply text-sm opacity-75;
}
.footnote-backref {
  display: none;
}
</style>

---
transition: slide-up
level: 2
---

# Database

 - PostgreSQLを使用できる
 - Webコンソールの作りが良いのでSQLクライアントは不要
 - クライアントから直接アクセス可能 & セキュリティ面も安全に実装可能
   - Supabase自体が認証の情報を持っているので次のような設定が可能 


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

# Databaseのセキュリティポリシーの設定①


 - 以下のSQLを実行して、tableを作成
 - ```sql
    create table
      public.items (
        id integer not null default nextval('items_id_seq'::regclass),
        user_id uuid not null,
        title text not null,
        url text not null,
        favIconUrl text null,
        created timestamp with time zone not null default current_timestamp,
        constraint items_pkey primary key (id)
      ) tablespace pg_default;
    ```


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

# Databaseのセキュリティポリシーの設定②

- 以下のSQLを実行して、tableにセキュリティポリシーを設定
- ```sql
  CREATE policy "All own items" 
  ON items
  FOR ALL
  USING ( auth.uid() = user_id );
  ```
- 上記を設定することで、**items.user_id == 認証済みのuid**のレコードのみアクセス可能な設定になる

<br/>

<v-clicks depth="2">

 - SupabaseのDatabaseクライントを使用してSQLを実行すると以下の動作になる
   - ■ コード
     - ```ts
       const { data, error } = await supabase.from('items').select('*')
       ```
   - ■ 実際に実行されるSQL
     - ```sql
        SELECT * FROM items WHERE auth.uid() = items.user_id
       ```
</v-clicks>

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

# Databaseの型安全①

- Supabaseは公式でDatabaseの設計からTypeScriptの型変換をサポートしている

<v-clicks depth="1">

- 以下のコマンドでログイン
  - ```bash
    $ npx supabase login
    ```  
- 以下のコマンドで初期設定
  - ```bash
    $ npx supabase init 
    $ npx supabase link --project-ref <プロジェクトのID>
    ```
- 以下のコマンドでTypeScriptの型情報を生成
  - ```bash
    $ npx supabase gen types typescript --linked > schema.ts
    ```
  - 生成されたファイル → [schema.ts](https://github.com/wheatandcat/MarkyLinky/blob/main/schema.ts)
 

</v-clicks>

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

# Databaseの型安全②

- 先程作成したファイルをimportして、型情報を設定する

<div class="px-10">

```ts {all|2|4|all}
  import { createClient } from "@supabase/supabase-js";
  import type { Database } from "../schema";

  export const supabase = createClient<Database>(
    process.env.PLASMO_PUBLIC_SUPABASE_URL,
    process.env.PLASMO_PUBLIC_SUPABASE_KEY,
  );
```

</div>

<br/>

- これで補完が効くようになる

<div class="px-10">
  <img src="/screen_03.png" class="w-180">
</div>

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

# その他の特徴

- 簡単にローカル環境が構築できる
  - 参考: [Supabaseのローカル開発環境構築](https://zenn.dev/razokulover/articles/db984ebfcf4bf6)
- DB操作の基本APIを自動生成してくれる
  - 参考 [Serverless APIs](https://supabase.com/docs/guides/api)
- リアルタイムリスナーをサポート
  - 参考: [Supabase JSのリアルタイムリスナーを使ってみる](https://zenn.dev/k_kind/articles/supabase-realtime-postgres)
- 有料版なら自動でバックアップを取ってくれる
  - 参考: [Pricing & fees | Supabase](https://supabase.com/pricing)


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

# その他の機能紹介

## Storage

 - 画像、ビデオ、テキスト等のファイルが保存できる
 - セキュリティポリシーを設定することで、アクセス制限が可能
 - コンソール画面からバケットに対してアップロードできるファイルサイズや、ファイル形式を制限できる

## Edge Functions
 - FaaS
 - TypeScript、Deno、Wasmをサポート

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

# 実装

 - 以下のPRで実装している
   - [supabaseでログイン + データ同期機能を追加 by wheatandcat](https://github.com/wheatandcat/MarkyLinky/pull/16)
 - デモで以下を紹介
   - ログイン画面
   - データ同期

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

## まとめ

<br/>

 - Supabaseは個人開発で使うには、かなり良いサービス
   - コンソールが使いやすい
   - セキュリティ周りも、わかりやすい
   - 従量制課金では無いので、コストも安心
 - プロダクトで使う場合は制限周りを確認する必要がある
   - [Pricing & fees | Supabase](https://supabase.com/pricing)

<style>
a {
  color: #84b9cb;
  @apply font-500;
}

p {
  margin: 1rem !important;
}



span {
  font-size:0.5rem;
  line-height: 0.5rem !important;
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
