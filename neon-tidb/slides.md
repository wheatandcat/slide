---
theme: ./theme
class: text-center
background:
highlighter: shiki
lineNumbers: false
info: |
  ## PlanetScaleの無料プランがなくなるので、NeonとTiDBを試してみた
drawings:
  persist: false
title: |
  PlanetScaleの無料プランがなくなるので、NeonとTiDBを試してみた
colorSchema: dark
fonts:
  sans: Noto Sans Japanese
  serif: Roboto Slab
  mono: Fira Code
---

### PlanetScaleの無料プランがなくなるので、NeonとTiDBを試してみた

<div class="flex justify-center pt-10">
  <img
    class="w-100 pt-2"
    src="/logo.png"
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

- 📝 飯野陽平（[wheatandcat](https://github.com/wheatandcat))
- 🏢 会社: [合同会社UNICORN](https://www.unicornllc.dev/) 代表社員
- 📚 Blog: https://www.wheatandcat.me/
- 🛠 今までに作ったもの
  - [memoir](https://memoir-lp-mvbeacmwe-wheatandcat.vercel.app/)
  - [OOMAKA](https://oomaka.vercel.app)
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

# PlanetScaleとは

- クラウドベースのサーバーレスDB
- MySQLと互換性のあるインターフェースを持つ
- オートスケールやノンブロッキングスキーマの変更をサポート
- YoutubeやSlackなどの大量のデータを扱う企業が利用されている
- 詳細
  - [PlanetScale](https://planetscale.com/)
 - 軽くコンソールを見せてDEMO
   - https://app.planetscale.com/

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

# 無料プランがなくなる件

- ５GBまで無料で使用できたが、2024年4月で無料プランの提供が終了
  - https://planetscale.com/blog/planetscale-forever
- 最小プランでも月額$50/月くらいはかかる
- 個人開発で使うには結構辛い


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
  color: #fff !important;
  opacity: 1 !important;
}
</style>


---
layout: default
---

# 今回の開発で使えるDBサービスの条件


 - 今回は個人開発で使用する前提なので以下の条件で調査
   - 個人開発で使用する範疇なら無料で使用できるDBサービス
   - [Prisma](https://www.prisma.io/)を使用できる


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
  color: #fff !important;
  opacity: 1 !important;
}
</style>
---
layout: default
---

# 代替えの候補

   - [Neon](https://neon.tech/)
   - [TiDB Serverless](https://pingcap.co.jp/tidb-serverless-now-generally-available/)


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
  color: #fff !important;
  opacity: 1 !important;
}
</style>

---
layout: default
---

# Neonとは

 - サーバーレスのフルマネージドPostgreSQLサービス
 - コードはGitHubで公開されている
   - [neondatabase/neon](https://github.com/neondatabase/neon)
   - Rust製
 - AWS AuroraやAlloyDBと似た機能を持ったアーキテクチャを採用（詳しくは以下の記事を参照）
   - https://neon.tech/blog/architecture-decisions-in-neon
   - ストレージとコンピューティングを分離した構成で柔軟なスケーリングが可能
 - 軽くコンソールを見せてDEMO
   - https://console.neon.tech/app/projects

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
  color: #fff !important;
  opacity: 1 !important;
}
</style>


---
layout: default
---

# メリット・デメリット

 - メリット
   - 無料枠が**512MB**
   - ブランチングができるので、環境毎にDBを複製ことが可能
   - Webのコンソールの機能が充実していて以下の機能が使用できる
     - SQL editor
     - IP制限
     - 定期バックアップ
 - デメリット
   - 東京リージョンが無い
     - 日本で使用する場合はシンガポールリージョンが一番近くになる

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

# TiDB Serverlessとは

 - **MySQL互換のあるNewSQLデータベースサービス**
 - 高い分散性能を持っており、大規模プロジェクトでも使用されている
 - コードはGitHubで公開されている
   - https://github.com/pingcap/tidb
   - Go製
 - 詳細なアーキテクチャは以下の記事を参照
   - https://docs.pingcap.com/ja/tidb/stable/tidb-architecture#tidb-architecture
 - 軽くコンソールを見せてDEMO
   - https://tidbcloud.com/console/clusters

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
  color: #fff !important;
  opacity: 1 !important;
}
</style>


---
layout: default
---

# メリット・デメリット

 - メリット
   - 無料枠が**5000万リクエストユニット（RU）/月**
   - NewSQLなのにPrismaが使用できる
   - 自動でデータ分散管理されるためシャーディングが不要
   - Writeのスケールも可能
   - 柔軟なトランザクションの設定が用意されていて用途に合わせて変更可能
     - https://docs.pingcap.com/ja/tidb/stable/transaction-isolation-levels
   - 運営会社のPingCAPに日本支社ができたので日本語のドキュメントが充実している
     - https://docs.pingcap.com/ja/tidb/stable/overview
 - デメリット
   - MySQLは完全互換では無い（詳細は[こちら](https://docs.pingcap.com/ja/tidb/stable/mysql-compatibility)) 
   - 学習コストが高い
    - 参考記事:  [TiDBにおけるパフォーマンス検証の進め方とつまづきポイント](https://zenn.dev/levtech/articles/2de2a3294924e4) 

<style>
ul {
  padding-left: 1rem;
  margin-top: 0.1rem;
}
li {
  @apply font-300;
  font-size:1rem;
}
a {
  color: #84b9cb;
  @apply font-300;
}
</style>


---

## まとめ

 - 初めてNeonとTiDB Serverlessに触ったが、どちらも使いやすくて良かった
 - Webコンソール機能的にはNeonの方が充実していたが、東京リージョンがないのが結構痛い
 - 今回は**TiDB Serverless**を採用することにした
 - 途中移行は難しそうだが、新規プロジェクトでの採用は積極的に検討した方が良さそう
 - 特に**TiDB**のアーキテクチャは興味深いので、今後も追いかけていきたい


<style>
ul {
  padding-left: 1rem;
  margin-top: 0.1rem;
}
li {
  @apply font-300;
  font-size:1rem;
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
