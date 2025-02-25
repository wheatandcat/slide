---
theme: ./theme
class: text-center
background:
highlighter: shiki
lineNumbers: false
info: |
  ## 1年半放置したExpo製アプリを最新化してみた
drawings:
  persist: false
title: |
    1年半放置したExpo製アプリを最新化してみた
colorSchema: dark
fonts:
  sans: Noto Sans Japanese
  serif: Roboto Slab
  mono: Fira Code
---

### 1年半放置したExpo製アプリを最新化してみた

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
 - Expoとは？
   - React Nativeを使用したアプリ開発を支える代表的なエコシステム
   - Expo SDKを使用することで、本来必要な開発をかなり省略できる
     - 省略できる開発の例
       - 公式がBuild環境のサーバーを提供
       - テストアプリの配布機能をサポート
       - Push通知等のプラットフォーム固有の開発をExpo側で抽象化して提供
       - etc...
   - 現在はReact Nativeの公式でもExpoを使用した開発を推奨している

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

h2 {
  color:rgb(182, 45, 45) !important;
  font-weight: 700 !important;
}
</style>

---

# 🤮 ローカルでビルドが出来なくなる
  - Expo SDK 48 → 52までの間で[EAS Build](https://docs.expo.dev/build/introduction/)の対応が必須になった
  - 元々あったExpo Goベースの開発はあくまでデバッグ用という立ち位置になり、ネイティブ周りの機能を修正したアプリはビルドできなくなった
  - Expo SDK 48の時点で本番ビルドはEAS Buildに移行済みだったが、EAS Buildで実行してもエラーになり、ローカルでもビルドできない
  - そもそもデバッグできない状態になり、詰みの状態が発生

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
  color: red !important;
  opacity: 1 !important;
}
</style>


---

# 😭 Expoの一部ライブラリが非推奨になる
  - Expo SDK 48 → 52までの間で[expo-auth-session](https://docs.expo.dev/versions/latest/sdk/auth-session/)の`expo-auth-session/providers/google`が非推奨になった
  - 具体的には、以前まではExpo更新のライブラリのみGoogleログインが可能だったが、出来なくなり代替で[@react-native-google-signin/google-signin](https://react-native-google-signin.github.io/docs/setting-up/expo)の使用が必須になった
  - その他の一部ライブラリでも廃止、仕様変更が発生がしていた

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
  - 以前は[react-navigation](https://reactnavigation.org/docs/getting-started)が最もよく使われているライブラリだった
  - 現在は[expo-router](https://docs.expo.dev/versions/latest/sdk/router/)が公式が提供しているライブラリとして推奨されている
  - しかも、expo-routerは`ファイルベースルーティング`を採用しているので、ディレクトリ構造の変更も必要
  - ファイルベースルーティングとは？
    - ディレクトリ構造が、そのまま画面のルーティングに反映される方式
    - Next.jsやNuxt.js等の採用されている方式

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
  - Expo SDK 48 → 52の移行でReact、React Nativeのバージョンが上がった
  - `defaultProps`の非推奨化など警告がでるようになり、一部コード修正が発生

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
  - 以前はフロントエンドのディレクトリ構造は[Atomic Design](https://atomicdesign.bradfrost.com/chapter-2/)が流行っていた
  - 現状のトレンドは以下
    - [Feature Sliced Design](https://feature-sliced.design/)
    - [Screaming Architecture](https://dev.to/profydev/screaming-architecture-evolution-of-a-react-folder-structure-4g25)（日本だとFeature型と呼ばれている事が多い）
  - トレンドが変わった理由
    - Atomic Designの定義が複雑でチーム開発でうまく回せないケースが多い
    - 後からの開発でコンポーネントの機能拡張した際に、ディレクトリ構造が変わる可能性があり、長期の開発では管理が難しくなる
    - 各画面との依存関係がわかりにくい等々



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
  - トレンドが変わった理由
    - 長期の開発をしていくとESLint & Prettierの設定の複雑になっていくケースが発生しやすい
    - ESLint & Prettierを使用するとPCに負荷がかかり開発に支障が出るケースがある
    - よりシンプル且つ、一括管理できるBiomeの方が採用されるようになった


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

# 🤔 使っていたライブラリが開発停止になる
  - 開発時はグローバルな状態管理は[Recoil](https://github.com/facebookexperimental/Recoil)が最もよく使われていた
  - Facebookが開発しているライブラリで、ほぼ公式扱いだったが...
  - その後の大規模レイオフで全開発者が解雇され開発停止になった
  - React 19では動作しないため、今後の移行が必須
  - 今後は[Jotai](https://jotai.org/)が使われていきそう



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

## このままでは開発できないので、諸々最新化してみる

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
 - Lint、Formatter: ESLint、Prettier → Biome
 - パッケージマネージャ: yarn → pnpm
 - ※まだReact19まで猶予があるので、**Recoil**の移行は一旦後回し

<br/>

 ■ リポジトリ
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
clicks: 1
---

# 起動まで①

Expoには、バージョンアップ時のマイグレーションを自動で行うコマンドが用意されている


以下のコマンドでSDKの最新化 & ライブラリのバージョンの依存関係を更新

```bash
$ npx expo install expo@latest
$ npx expo install --fix
```

以下のコマンドでドキュメントに記載されているチェックを行い、NGが出ている箇所を修正

```bash
$ npx expo-doctor
```

 - 参考
   - [Expo Doctor](https://docs.expo.dev/develop/tools/#expo-doctor)


<br>
<div v-click="1" v-if="$slidev.nav.clicks === 1">

ただ今回のケースでは、これをやってもビルドが通らなかった 😢 <br/>
なので、新規でExpoのプロジェクトを作成して徐々に既存のコードを移行する手法で対応

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
  color: #fff !important;
  opacity: 1 !important;
}
</style>


---

# 起動まで②

以下のページを参考に、Expo Routerのサンプルアプリを作成
 - [Install Expo Router - Expo Documentation](https://docs.expo.dev/router/installation/)

ここから徐々に既存のコードを移行していった

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

# ディレクトリ構造①


■ 以前のディレクトリ構造
```bash {all|3-15|4-9}
.
├── assets
└── src
    ├── components
    │   ├── atoms
    │   ├── molecules
    │   ├── organisms
    │   ├── pages
    │   └── templates
    ├── containers
    ├── hooks
    ├── img
    ├── lib
    ├── queries
    └─ store
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

# ディレクトリ構造②


■ 現在のディレクトリ構造
```bash {all|2-4|8-10|12-17}
.
├── app
│   └── (app)
│       └── search
├── assets
│   ├── fonts
│   └── img
├── components
│   ├── elements
│   └── layouts
├── containers
├── features
│   ├── home
│   │   └── components
│   └── search
│       ├── components
│       └── hooks
├── hooks
├── lib
├── queries
└── store
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

# Lint、Formatterの移行

 - 以下のページを参考に[Biome](https://biomejs.dev/)に移行
   - [Getting Started | Biome](https://biomejs.dev/guides/getting-started/)
 - 今回のコードでは軽微な修正のみだったので基本は移行後に、以下のコマンドで自動で修正できた
   - ```bash
     $ npx @biomejs/biome check --write ./
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
layout: fact
class: "text-center"
---

# デモ

## 現在の動作するところまで確認

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
- 正直、ローカルビルドができなくなるのは想定していなかったので、かなり困った
- フレームワークとしての強みはかなりあるが、反面フレームワークで強制される部分が大きいので、開発に間を空けすぎると復帰が難しくなる
- バックエンドと比較してフロントエンドはトレンドの移り変わりが激しいのを再認識した


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
