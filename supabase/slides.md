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
class: px-20
---

# Themes

Slidev comes with powerful theming support. Themes can provide styles, layouts, components, or even configurations for tools. Switching between themes by just **one edit** in your frontmatter:

<div grid="~ cols-2 gap-2" m="-t-2">

```yaml
---
theme: default
---
```

```yaml
---
theme: seriph
---
```

<img border="rounded" src="https://github.com/slidevjs/themes/blob/main/screenshots/theme-default/01.png?raw=true">

<img border="rounded" src="https://github.com/slidevjs/themes/blob/main/screenshots/theme-seriph/01.png?raw=true">

</div>

Read more about [How to use a theme](https://sli.dev/themes/use.html) and
check out the [Awesome Themes Gallery](https://sli.dev/themes/gallery.html).

---
preload: false
---

# Animations

Animations are powered by [@vueuse/motion](https://motion.vueuse.org/).

```html
<div
  v-motion
  :initial="{ x: -80 }"
  :enter="{ x: 0 }">
  Slidev
</div>
```

<div class="w-60 relative mt-6">
  <div class="relative w-40 h-40">
    <img
      v-motion
      :initial="{ x: 800, y: -100, scale: 1.5, rotate: -50 }"
      :enter="final"
      class="absolute top-0 left-0 right-0 bottom-0"
      src="https://sli.dev/logo-square.png"
    />
    <img
      v-motion
      :initial="{ y: 500, x: -100, scale: 2 }"
      :enter="final"
      class="absolute top-0 left-0 right-0 bottom-0"
      src="https://sli.dev/logo-circle.png"
    />
    <img
      v-motion
      :initial="{ x: 600, y: 400, scale: 2, rotate: 100 }"
      :enter="final"
      class="absolute top-0 left-0 right-0 bottom-0"
      src="https://sli.dev/logo-triangle.png"
    />
  </div>

  <div
    class="text-5xl absolute top-14 left-40 text-[#2B90B6] -z-1"
    v-motion
    :initial="{ x: -80, opacity: 0}"
    :enter="{ x: 0, opacity: 1, transition: { delay: 2000, duration: 1000 } }">
    Slidev
  </div>
</div>

<!-- vue script setup scripts can be directly used in markdown, and will only affects current page -->
<script setup lang="ts">
const final = {
  x: 0,
  y: 0,
  rotate: 0,
  scale: 1,
  transition: {
    type: 'spring',
    damping: 10,
    stiffness: 20,
    mass: 2
  }
}
</script>

<div
  v-motion
  :initial="{ x:35, y: 40, opacity: 0}"
  :enter="{ y: 0, opacity: 1, transition: { delay: 3500 } }">

[Learn More](https://sli.dev/guide/animations.html#motion)

</div>

---

# LaTeX

LaTeX is supported out-of-box powered by [KaTeX](https://katex.org/).

<br>

Inline $\sqrt{3x-1}+(1+x)^2$

Block
$$
\begin{array}{c}

\nabla \times \vec{\mathbf{B}} -\, \frac1c\, \frac{\partial\vec{\mathbf{E}}}{\partial t} &
= \frac{4\pi}{c}\vec{\mathbf{j}}    \nabla \cdot \vec{\mathbf{E}} & = 4 \pi \rho \\

\nabla \times \vec{\mathbf{E}}\, +\, \frac1c\, \frac{\partial\vec{\mathbf{B}}}{\partial t} & = \vec{\mathbf{0}} \\

\nabla \cdot \vec{\mathbf{B}} & = 0

\end{array}
$$

<br>

[Learn more](https://sli.dev/guide/syntax#latex)

---

# Diagrams

You can create diagrams / graphs from textual descriptions, directly in your Markdown.

<div class="grid grid-cols-3 gap-10 pt-4 -mb-6">

```mermaid {scale: 0.5}
sequenceDiagram
    Alice->John: Hello John, how are you?
    Note over Alice,John: A typical interaction
```

```mermaid {theme: 'neutral', scale: 0.8}
graph TD
B[Text] --> C{Decision}
C -->|One| D[Result 1]
C -->|Two| E[Result 2]
```

```mermaid
mindmap
  root((mindmap))
    Origins
      Long history
      ::icon(fa fa-book)
      Popularisation
        British popular psychology author Tony Buzan
    Research
      On effectivness<br/>and features
      On Automatic creation
        Uses
            Creative techniques
            Strategic planning
            Argument mapping
    Tools
      Pen and paper
      Mermaid
```

```plantuml {scale: 0.7}
@startuml

package "Some Group" {
  HTTP - [First Component]
  [Another Component]
}

node "Other Groups" {
  FTP - [Second Component]
  [First Component] --> FTP
}

cloud {
  [Example 1]
}


database "MySql" {
  folder "This is my folder" {
    [Folder 3]
  }
  frame "Foo" {
    [Frame 4]
  }
}


[Another Component] --> [Example 1]
[Example 1] --> [Folder 3]
[Folder 3] --> [Frame 4]

@enduml
```

</div>

[Learn More](https://sli.dev/guide/syntax.html#diagrams)

---
src: ./pages/multiple-entries.md
hide: false
---

---
layout: center
class: text-center
---

# Learn More

[Documentations](https://sli.dev) · [GitHub](https://github.com/slidevjs/slidev) · [Showcases](https://sli.dev/showcases.html)
