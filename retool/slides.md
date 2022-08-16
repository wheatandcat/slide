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
 - 表示周りではjsもサポートしているので、柔軟性も高い  

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

 - 実際にプロジェクトに[opentelemetry-go](https://github.com/open-telemetry/opentelemetry-go)を実装したみた。<br/>
 - 構成は以下の通り
   - プロジェクト: [memoir-backend](https://github.com/wheatandcat/memoir-backend)
   - フレームワーク: **gqlgen**
   - ベンダー: [Cloud Trace](https://cloud.google.com/trace?hl=ja)
      - 最初は[DatadogのAPM](https://www.datadoghq.com/ja/dg/apm/benefits/?utm_source=advertisement&utm_medium=search&utm_campaign=dg-google-japan-apac-apm&utm_keyword=apm%20datadog&utm_matchtype=p&utm_campaignid=9360752627&utm_adgroupid=102783316219)を想定していたが、**Cloud Run For Manager**をサポートしていなかったので😓、Cloud Traceで実装

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

<br/>

 - PR
   - https://github.com/wheatandcat/memoir-backend/pull/128
 - 以下を解説
   - gqlgenのトレースのハンドリングの解説
   - Cloud Traceの出力のデモ

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

# Cloud Traceを実装してみての感想と課題

 - トレース情報が可視化されて、**各APIの処理速度を直感的にわかるようになった**
 - 今回のプロジェクトはAPIの数も少ないのでトレース情報のみでも十分に解析可能だが、以下のようなケースでは**別のアプローチを考える必要がある**
   - トレース情報が大雑把すぎる。具体的に遅い処理を検知したい
   - APIや処理数が膨大で漠然と全体的に遅い
   - ユーザーによって処理が遅い
 - 上記のケースでは[Cloud Profiler](https://cloud.google.com/profiler/docs/about-profiler?hl=ja)が有効なので紹介

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

# Cloud Profilerとは

 - **Cloud Profiler**は、本番環境のアプリケーションから**CPU 使用率やメモリ割り当てなどの情報を継続的に収集できるサービス**
 - トレースのような大雑把な情報は出力できないが、**ピンポイントにボトルネックになっている処理の検知が行える**
 - 料金は**無料**なので、取り敢えず実装しておいても損は無さそう

<br/>
<br/>
<br/>
<br/>
<br/>

[Learn More](https://cloud.google.com/profiler/docs/about-profiler?hl=ja)

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

# 実装してみた

<br/>

 - 以下を参考に実装
   - https://cloud.google.com/profiler/docs/profiling-go?hl=ja
 - 以下を解説
   - Cloud Profilerのデモ
     - memoir-backendは処理がシンプル過ぎて、解説向きの情報が無いので以下で解説
   - 以下を参考に実際の利用方法の解説
     - [チュートリアル: Go アプリの最適化](https://cloud.google.com/profiler/docs/quickstart-go-app?hl=ja)

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

# おまけ

<br/>

 - 今回、実装までは行わなかったが、今回紹介した**Cloud Trace**と**Cloud Profiler**などの情報をまとめて、**Cloud Monitoring**でアラートもできそう
   - https://cloud.google.com/architecture/integrating-monitoring-logging-trace-observability-and-alerting?hl=ja
 - **Cloud Monitoring**の説明は以下を参照
    - https://cloud.google.com/monitoring/monitor-compute-engine-virtual-machine

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

 - **OpenTelemetry**は現状デファクトなので、理解しておいたほうが良さそう
 - パフォーマンス解析のアプローチについて理解できた
 - 早くDatadogのAPMが**Cloud Run For Manager**をサポートして欲しい
   - GKE構成にすれば使えるけど、個人プロジェクトで、そこまで管理コストをかけたくない 😓


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


