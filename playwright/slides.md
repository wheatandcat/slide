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
  # Playwrightの紹介
# persist drawings in exports and build
drawings:
  persist: false
title:  Playwrightの紹介
layout: intro
colorSchema: "light"
---

## **Playwright**の紹介

<div class="flex justify-center">
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
- 🏢 個人事業主 → 法人設立（合同会社UNICORN 代表社員）
- 💻 Work: シェアフル株式会社CTO
- 📚 Blog: https://www.wheatandcat.me/
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

## **Playwright**とは？

<br/>

- E2EテストのためのNode.jsのライブラリ
- Chromium、Firefox、および WebKit ブラウザをサポート
- テストコードをブラウザ操作から自動生成できるのが強み
- Microsoftが作成
- 開発に元Puppeteerの開発者がいるため、インタフェースが似ている

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

## 導入

<br/>

以下のコマンで実行で導入可能

```bash
npm init playwright@latest
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
  margin-top: 0.25rem;
}
</style>

---

## コード

以下のコードで実行できる

```ts
import { test, expect } from '@playwright/test';

test.describe("check website", () => {
  test('has title', async ({ page }) => {
    await page.goto('https://playwright.dev/');

    // Expect a title "to contain" a substring.
    await expect(page).toHaveTitle(/Playwright/);
  });

  test('get started link', async ({ page }) => {
    await page.goto('https://playwright.dev/');

    // Click the get started link.
    await page.getByRole('link', { name: 'Get started' }).click();

    // Expects the URL to contain intro.
    await expect(page).toHaveURL(/.*intro/);
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
  margin-top: 0.25rem;
}
</style>


---

## 実行①

<br/>
以下のコマンドで実行
<br/>
<br/>

```bash
playwright test
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
  margin-top: 0.25rem;
}
</style>


---

## 実行②

<br/>
テスト結果は以下のように確認できる
<br/>
<br/>


<div class="flex justify-center">
  <img
    class="w-full pt-2"
    src="/test_r_01.png"
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

## 実行③

<br/>
対象のテストをクリックで詳細も確認できる

<br/>
<div class="flex justify-center">
  <img
    class="w-110 pt-2"
    src="/test_r_02.png"
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

## 実行④

<br/>
Trace機能を使用して確認
<br/>
<br/>

```bash
playwright test --trace on
npx playwright show-report
```

<div class="flex justify-center">
  <img
    class="w-110 pt-2"
    src="/test_r_04.png"
  />
</div>
<br/>
<hr/>

 - [Trace Viewer | Playwright](https://playwright.dev/docs/trace-viewer-intro)


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

## テストコードの自動生成

<br/>
以下のコマンドで実行
<br/>
<br/>

```bash
npx playwright codegen
``` 

<div class="flex justify-center">
  <img
    class="w-100 pt-2"
    src="/test_r_03.png"
  />
</div>


<div className="text-center pt-4">※デモをやる</div>

<br/>
<hr/>

 - [Test Generator | Playwright](https://playwright.dev/docs/codegen)


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

## 実装

<br/>

 - 自作のアプリに導入してみたので紹介
 - PR: [e2eで保存したデータを検証](https://github.com/wheatandcat/todo/pull/31)


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

## 実装したモチベーション

<br/>

 - アプリで使用している[markdown-to-jsx](https://www.npmjs.com/package/markdown-to-jsx)がユニットテストで動作しない
 - Markdownの入力をparseしてTODO管理するアプリなので、**markdown-to-jsx**の入/出力が重要
 - なので、**Playwright**で継続的にテストできるように実装
 

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

## 実装内容

※デモしながら紹介（トレースも見せる）

 - テストファイルは以下を参照
   - [e2e/todo.spec.ts](https://github.com/wheatandcat/todo/blob/05751f6f78fe45b43348c3bc729c818a8cf89878/e2e/todo.spec.ts)
   - localStorageのテストは`evaluate`を使用
     - [Evaluating JavaScript | Playwright](https://playwright.dev/docs/evaluating)
 - CIで実行は以下を参照
   - [.github/workflows/playwright.yml](https://github.com/wheatandcat/todo/blob/eaa55b1c60928c115b538f70b355b34f9f421f6d/.github/workflows/playwright.yml)
   - 実行結果は、[こちら](https://github.com/wheatandcat/todo/actions/runs/4455759854/jobs/7825771527) 

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

## まとめ

<br/>

 - E2Eテストは保守が大変だが、Playwrightはテストコードの生成機能があるので保守しやすい
 - 複数のブラウザをサポートしているので安全性が高い
 - トレース機能があるのでCIでコケた時も原因の発見が容易

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
