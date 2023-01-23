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
  ## Vitestの紹介
# persist drawings in exports and build
drawings:
  persist: false
title:  Vitestの紹介
layout: intro
colorSchema: "light"
---

## **Vitest**の紹介

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
---

# **Vitest**とは

<br/>

- [Vitest](https://vitest.dev/)は[Vite](https://ja.vitejs.dev/)環境で動作する高速なテストフレームワーク
- 領域的には[Jest](https://jestjs.io/ja/)と同じ
- 特徴は実行速度の速さ。以下、参考記事
  - [Vitest はどれくらい早いのか ~ Jest と比較 ~](https://zenn.dev/jay_es/articles/2021-12-22-vitest-comparison)
  - 特にwatchモードが高速
- その他にも細かいチューニングがされている


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

# **Vitest**を導入してみる①

<br/>

導入は以下を参照。

 - [Getting Started | Guide | Vitest](https://vitest.dev/guide/)




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
}
</style>


---

# **Vitest**を導入してみる②

<br/>

コードは以下みたいな感じで書ける。

```ts
import { describe, it, expect } from 'vitest'
import { add } from "./calc"

describe('suite', () => {
  it('concurrent test 1', async () => {
      const r = add(1, 2);
      expect(r).toEqual(3)
   })
})
```

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
}
</style>

---

# **Vitest**を導入してみる③

<br/>

コンポーネントのテストなら以下みたいな感じ。

```tsx
import { describe, expect, it } from "vitest";
import { render, screen } from "@testing-library/react";
import Demo from "./Demo";

describe("Demo", () => {
  it("タイトルに、「デモ」が表示さてている", () => {
    const props = {
      title: "デモ"
    };
    render(<Demo {...props} />);

    expect(screen.getByText(/デモ/i)).toBeTruthy();
  });
});

```

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
}
</style>


---

# **Vitest**を導入してみる④

<br/>

テストの実行以下のコマンドでOK 👌。

```bash
$ vitest
```

デフォルトで**watchモード**で起動。

```bash
$ vitest

 DEV  v0.27.1 ./demo

 ✓ src/lib/calc.ts (2)
 ✓ src/components/organisms/Demo.test.tsx (1)

 Test Files  2 passed (2)
      Tests  2 passed (2)
   Start at  23:12:20
   Duration  3.25s (transform 1.06s, setup 712ms, collect 725ms, tests 70ms)
```


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
}
</style>


---

# カバレッジ/Mocking/Testing Type

<br/>

以下のあたりはJestとほぼ同様に使用できる。
 - [Coverage](https://vitest.dev/guide/coverage.html)
 - [Mocking](https://vitest.dev/guide/mocking.html)
 - [Testing Types](https://vitest.dev/guide/testing-types.html)


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
}
</style>

---

# **Vitest UI**

<br/>

VitestにUIからテスト実行/確認行える機能がある。
 - [Vitest UI](https://vitest.dev/guide/ui.html)

以下のコマンドで実行。 
 
```bash
$ vitest --ui
``` 

<br/>
 
※デモで説明。

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
}
</style>

---

# **In-source testing**

<br/>

好みは別れるが、Rustみたいにコード上にテストコードを書くこともできる。


```ts
// the implementation
export function add(...args: number[]) {
  return args.reduce((a, b) => a + b, 0)
}

// in-source test suites
if (import.meta.vitest) {
  const { it, expect } = import.meta.vitest
  it('add', () => {
    expect(add()).toBe(0)
    expect(add(1)).toBe(1)
    expect(add(1, 2, 3)).toBe(6)
  })
}
``` 
 
 - [In-source testing | Guide | Vitest](https://vitest.dev/guide/in-source.html)


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
}
</style>


---

# **Debugging**

<br/>

テストコードでデバッガも使用できる。
 - [Debugging | Guide | Vitest](https://vitest.dev/guide/debugging.html)

<br/>
 
※デモで説明。

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
}
</style>

---

# まとめ

<br/>

- Jest互換なので、移行も比較的に容易に行えるのでおすすめ。
- 機能もかなり充実しているのでプロダクトで使っても、問題なさ気。
- 現状だとWebpack→Vite移行が進んでいるので、合わせてテストフレームワークも移行を検討すると良いかなと思います。

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
