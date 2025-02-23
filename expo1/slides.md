---
theme: ./theme
class: text-center
background:
highlighter: shiki
lineNumbers: false
info: |
  ## 1年半放置したExpo制アプリを最新化する
drawings:
  persist: false
title: |
    1年半放置したExpo制アプリを最新化する
colorSchema: dark
fonts:
  sans: Noto Sans Japanese
  serif: Roboto Slab
  mono: Fira Code
---

### 1年半放置したExpo制アプリを最新化してみた

<div class="flex justify-center pt-10">
  <img
    class="w-50 pt-2"
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

# あらすじ①

<div class="flex pb-5">
  <img
    class="w-120 pt-2"
    src="/screen_01.png"
  />
</div>



- 2022年に**memoir**をリリース
- 参考リンク
  - [memoir](https://www.memoir-app.dev/)
  - [【夫婦で開発】1年かけて1週間を振り返えるアプリを本気で開発してみた](https://zenn.dev/wheatandcat/articles/20220503-memoir)


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

# あらすじ②



 - 技術スタック
  - [Expo](https://expo.dev/)
  - ログイン
    - iOS: 
    - Android: 

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

# あらすじ③

 - 2023年までは定期的に更新していたが、それ以降は他の個人開発に時間を割いていて更新を止めていた
 - 間に作っていた個人制作物
   - [自分専用todo](https://github.com/wheatandcat/todo)
   - [MarkyLinky](https://github.com/wheatandcat/MarkyLinky)
   - [OOMAKA](https://oomaka.vercel.app)
   - [STOCK KEEPER](https://github.com/wheatandcat/stock-keeper)
 
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
layout: fact
class: "text-center"
---

## 開発を1年半サボると、どういうことが起きるのか？

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

---

# 🤮 アプリのローカルでビルドが出来なくなる
  - Expo SDK 48 → 52までの間で[EAS Build](https://docs.expo.dev/build/introduction/)の対応が必須になった
  - 元々あったExpo Goベースの開発はあくまでデバッグ用という立ち位置になりネイティブ周りの機能を修正したアプリはビルドできなくなった
  - Expo SDK 48の時点で本番ビルドはEAS Buildに移行済みだったが、EAS Buildで実行してもエラーになり、ローカルでもビルドできないので、そもそもデバッグできない状態になっていた

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

# 😭 Expoの一部ライブラリが非推奨になる
  - Expo SDK 48 → 52までの間で[expo-auth-session](https://docs.expo.dev/versions/latest/sdk/auth-session/)の`expo-auth-session/providers/google`が非推奨になった
  - 具体的には、以前まではExpo更新のライブラリのみGoogleログインが可能だったが、出来なくなり代替で[@react-native-google-signin/google-signin](https://react-native-google-signin.github.io/docs/setting-up/expo)の使用が必須になった

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

# 😭 ナビゲーションライブラリのトレンドが変わる
  - 元々、[react-navigation](https://reactnavigation.org/docs/getting-started)が最もよく使われているライブラリだった
  - 現在は[expo-router](https://docs.expo.dev/versions/latest/sdk/router/)という公式が提供しているライブラリが推奨されている
  - しかも、expo-routerは`ファイルベースルーティング`を採用しているので、ディレクトリ構造の変更も必要

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

# 🙁 Reactのバージョンが変わり、非推奨が発生
  - Expo SDK 48 → 52の移行でReact、React Nativeのバージョンも上がった
  - `defaultProps`の非推奨化など警告がでるようになった

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

# 🤔 ディレクトリ構造のトレンドが変わる
  - アプリを作成していた頃は、フロントエンドのディレクトリ構造は`Atomic Design`が流行っていた
  - 現状のトレンドは以下
    - [Feature Sliced Design](https://feature-sliced.design/)
    - [Screaming Architecture](https://dev.to/profydev/screaming-architecture-evolution-of-a-react-folder-structure-4g25)

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

# 🤔 Lint、Formatterのトレンドが変わる
  - 以前は[ESLint](https://eslint.org/)と[Prettier](https://prettier.io/)を使っていた
  - 現在は[Biome](https://biomejs.dev/ja/)がトレンド

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

# 🤔 パッケージマネージャのトレンドが変わる
  - 以前は[yarn](https://yarnpkg.com/)を使っていた
  - 現在は[pnpm](https://pnpm.io/)がトレンド

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
layout: fact
class: "text-center"
---

## 問題を解決するために、アプリを最新化してみた

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



---

# 最新化後の構成


 - Expo SDK: 48 → 52
 - ナビゲーションライブラリ: react-navigation → expo-router
 - ディレクトリ構造: Atomic Design → Feature型
 - Lint、Formatter: ESLint → Biome
 - パッケージマネージャ: yarn → pnpm

 - リポジトリ
   - 更新前: [リンク](https://github.com/wheatandcat/memoir/tree/3cc1db4959b54415195158fd3185440653595bb8)
   - 更新後: [リンク](https://github.com/wheatandcat/memoir/tree/17dc876e90ab3b243fe39ccb1af52bad600d2841)


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

# 起動まで①

Expoには以下のコマンド

```bash
$ npx expo install expo@latest
$ npx expo install --fix
```

```bash
$ npx expo-doctor
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
  color: #fff !important;
  opacity: 1 !important;
}
</style>


---

# 起動まで②

一旦、eas buildは諦め、Expo Goで起動できるようにして試してみる


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

# ディレクトリ構造

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

# Googleログイン

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

# Lint、Formatterの移行

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
layout: fact
class: "text-center"
---

# デモ

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


---
layout: default
---

# まとめ
- Expoのアプリの開発を1年半放置すると、結構な地獄になる
- フレームワークとしての強みはかなりあるが反面こういうデメリットも大きい



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
