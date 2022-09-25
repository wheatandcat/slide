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
  ## mswでフロントエンドのインテグレーションテストを実装する
# persist drawings in exports and build
drawings:
  persist: false
title: mswでフロントエンドのインテグレーションテストを実装する
layout: intro
colorSchema: "light"
---

## **msw**でフロントエンドの<br/>インテグレーションテストを実装する

<div class="flex justify-center">
  <img
    class="w-30 pt-2"
    src="/logo.png"
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

# **msw**とは

<br/>

- **msw**(Mock Service Worker)は、ネットワークレベルでAPIリクエストをインターセプトしてmockのデータを返すためのライブラリ
- **Service Worker** を使用しているので、別プロセスでローカルのサーバーを立ち上げる必要が無く手軽に利用できる
- フロントエンドの**テストコード**や[Stroybook](https://storybook.js.org/)などでも利用可能
- デフォルトで**RESTful API**と**GraphQL**をサポートしている

<br/>
<br/>
<br/>

- [msw](https://mswjs.io/)
- [Service Worker とは](https://ugo.tokyo/about-service-worker/)
- [msw Choose an API](https://mswjs.io/docs/getting-started/mocks)

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


</style>

---
layout: image-right
---

### インテグレーションテストとは？

<div class="absolute w-full">
  <div class="absolute right-20">
    <img
      class="w-100"
      src="/test_001.svg"
    />
  </div>
</div>

- フロントエンドのテストは主に以下の4つに分類される
  - End to End
  - Integration
  - Unit
  - Static
- 上位レイヤーに行くほど以下の特徴がある
  - フィードバックの速度は遅い
  - 実装コストは高い
  - 信頼性は向上する

<br/>
<br/>

- [The Testing Trophy and Testing Classifications](https://kentcdodds.com/blog/the-testing-trophy-and-testing-classifications)


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
  font-size:1rem;
}
</style>

---

# インテグレーションテストのこれまで ①

<br/>

- msw導入前だと各APIを**jest**のmock機能を使用してAPIのコールメソッドを、すべてmockさせて実装させていく必要があった
- コード的には次のようになっていた

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


</style>

---

# インテグレーションテストのこれまで ②

```ts {all|2-14|all}
describe("components/pages/ItemDetail/Connected.tsx", () => {
  jest.spyOn(queries, "useItemQuery").mockImplementation((): any => ({
    loading: false,
    data: {
      item: {
        id: "1",
        title: "本を読む",
        categoryID: 2,
        date: "2021-01-01T00:00:00+09:00",
      },
    },
    error: undefined,
    refetch: jest.fn(),
  }));

  const wrapper = shallow(<Connected {...propsData()} />);

  it("正常にrenderすること", () => {
    expect(wrapper).toMatchSnapshot();
  });
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
  font-size:1rem;
}
</style>


---

# モチベーション

<br/>

- 今までmock作業で実装に時間の掛かったインテグレーションテストを簡単に実装できる状態にしたい
- また、実際の動作に伴ったシナリオテストを実装できる状態にしたい

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


</style>

---

# 実装に使用したライブラリ

<br/>

- [msw](https://mswjs.io/)
- [typed-document-node](https://www.the-guild.dev/graphql/codegen/plugins/typescript/typed-document-node)
- [graphql-codegen-typescript-mock-data](https://github.com/ardeois/graphql-codegen-typescript-mock-data)
- [testing-library/react-native](https://testing-library.com/)

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
  font-size:1rem;
}
</style>

---

# 実装PR

<br/>

- [typed-document-nodeへの移行](https://github.com/wheatandcat/memoir/pull/248)
- [mswを導入してGraphQLをモックしたテストコードを書く①](https://github.com/wheatandcat/memoir/pull/249)
- [mswを導入してGraphQLをモックしたテストコードを書く②](https://github.com/wheatandcat/memoir/pull/251)

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
  font-size:1rem;
}
</style>

---

# 実装してみた ①

<br/>

- まずは、[typescript-react-apollo](https://www.the-guild.dev/graphql/codegen/plugins/typescript/typescript-react-apollo)→[typed-document-node](https://www.the-guild.dev/graphql/codegen/plugins/typescript/typed-document-node)移行を実装
- PR: [typed-document-nodeへの移行](https://github.com/wheatandcat/memoir/pull/248)
- 実装の紹介
  - こちら、次のPRで使用する[graphql-codegen-typescript-mock-data](https://github.com/ardeois/graphql-codegen-typescript-mock-data)を使用しやすくするために移行
  - **typed-document-node**は特定のGraphQLクライアントに依存せずにGraphQLのtypeを自動生成してくれるcodegenのプラグイン

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

# 実装してみた ②

<br/>

- 次に、mswとgraphql-codegen-typescript-mock-dataを導入
- PR: [mswを導入してGraphQLをモックしたテストコードを書く①](https://github.com/wheatandcat/memoir/pull/249)
- 実装の紹介
  - **graphql-codegen-typescript-mock-data**は、GraphQLのSchema情報からダミーデータを生成してくれるライブラリ
  - これを利用することでmockデータを保守を自動生成で補うようにする
    - [参考コード](https://github.com/wheatandcat/memoir/blob/92684315ddf5da1a2cdebf866d425110b22ca3c5/src/mocks/handler.ts)
  - mswは以下の部分でテスト時に起動させる
    - [参考コード](https://github.com/wheatandcat/memoir/blob/92684315ddf5da1a2cdebf866d425110b22ca3c5/setupTests.js#L10-L18)
  - テストは以下の通りに記載
    - [参考コード](https://github.com/wheatandcat/memoir/blob/92684315ddf5da1a2cdebf866d425110b22ca3c5/src/components/pages/ItemDetail/__tests__/Connected.test.tsx)
  
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

# 実装してみた ③

<br/>

- 最後に、前のPRからの追加で、より正確なシナリオテストを実装
- PR: [mswを導入してGraphQLをモックしたテストコードを書く②](https://github.com/wheatandcat/memoir/pull/251)
- 実装の紹介
  - アイテムの更新のシナリオテストを追加
    - [参考コード](https://github.com/wheatandcat/memoir/blob/638e171636b5cb40e8c781181a4cf0cb11fc581b/src/components/pages/ItemDetail/__tests__/Connected.test.tsx)
  - [testing-library/react-native](https://testing-library.com/)を使用して各入力を設定
    - [参考コード](https://github.com/wheatandcat/memoir/blob/638e171636b5cb40e8c781181a4cf0cb11fc581b/src/components/pages/ItemDetail/__tests__/Connected.test.tsx#L94-L105)
  - 入力に設定した値と更新のAPI時に設定された値と**GraphQLのvariables**を比較して一致しているかテスト
    - [参考コード](https://github.com/wheatandcat/memoir/blob/638e171636b5cb40e8c781181a4cf0cb11fc581b/src/components/pages/ItemDetail/__tests__/Connected.test.tsx#L107-L116)

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

- [msw](https://mswjs.io/)を使えば気軽にインテグレーションテストを書けて、かなり良い。
- graphql-codegen周りの自動生成周りのツールと相性が良い
- テストから仕様が把握できるコードにしやすくなった

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
