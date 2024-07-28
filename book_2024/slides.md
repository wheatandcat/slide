---
theme: ./theme
class: text-center
background:
highlighter: shiki
lineNumbers: false
info: |
  ## 最近読んだ技術書を簡単紹介
drawings:
  persist: false
title: |
  最近読んだ技術書を簡単紹介
colorSchema: dark
fonts:
  sans: Noto Sans Japanese
  serif: Roboto Slab
  mono: Fira Code
---

### 最近読んだ技術書を簡単紹介

<div class="flex justify-center pt-10">
  <img
    class="w-50 pt-2"
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

# 今回のスライド
  - 技術系の知識のインプット元の情報をアウトプットしていないと思い、まとめました
  - 自分は主に以下の3つから情報を得ている
    - 技術書
    - Podcast
    - Webサイト
  - 2022〜2024年で読んで面白かった技術本を簡単に紹介
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
transition: fade-out 
layout: image-right
image: /screen_01.png
---

### オブジェクト指向UIデザイン 
#### ―使いやすいソフトウェアの原理

<br/>

 - オブジェクト指向 UI （OOUI）の解説本
 - 論理的にUI設計を行うための手法を学べるので、エンジニアがUI設計を理解するのに最適
 - 中盤からは特定の要件からオブジェクト指向 UIを設計するクイズ形式で進む感じになっているので、実践的にUIを学ぶことができる

<style>
h4 {
  color: #84b9cb;
  font-size: 16px !important;
}

ul {
  padding-left: 1rem;
  margin-top: 0.1rem;
}
li {
  @apply font-300;
  font-size:1.0rem;
}
a {
  color: #84b9cb;
  @apply font-300;
}
</style>

---
layout: image-right
image: /screen_02.png
---

### SCRUM BOOT CAMP THE BOOK
#### スクラムチームではじめるアジャイル開発
 - スクラムの基本的なイベントを学べる
 - マンガ形式 + 解説で進行されるのでスクラムの解説本の中では、かなり読みやすい
 - スクラムについて深く学ぶ本ではないが、全体像を把握するのに良い

<style>
h4 {
  color: #84b9cb;
  font-size: 16px !important;
}

ul {
  padding-left: 1rem;
  margin-top: 0.1rem;
}
li {
  @apply font-300;
  font-size:1.0rem;
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
layout: image-right
image: /screen_04.png
---

### The DevOps ハンドブック
#### 理論・原則・実践のすべて
 - アジェイルからの文脈でDevOpsについて知識をつけたかったので読んでみた
 - 前のページで紹介したスクラムの本は製品リリースまでの話を中心で運用開始後の話は無い
 - DevOpsは運用開始後に、どうサイクルを回すのかの話が中心 

<style>
h4 {
  color: #84b9cb;
  font-size: 16px !important;
}

ul {
  padding-left: 1rem;
  margin-top: 0.1rem;
}
li {
  @apply font-300;
  font-size:1.0rem;
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
layout: image-right
image: /screen_03.png
---

### チームトポロジー
#### 価値あるソフトウェアをすばやく届ける適応型組織設計
 - DevOpsの発展型の文脈で読んでみた
 - 開発のサイクルを適切に回すための最適になチームの形について解説している
 - スクラム、DevOpsの話の先にある、組織の成長、システムの大規模化の概念についての対策本
 - 本の中で各役割のチームや各コミュニケーションの定義に名前をつけていて、本を読んだもの同士で共通認識が持ちやすい


<style>
h4 {
  color: #84b9cb;
  font-size: 16px !important;
}

ul {
  padding-left: 1rem;
  margin-top: 0.1rem;
}
li {
  @apply font-300;
  font-size:1.0rem;
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
layout: image-right
image: /screen_07.png
---

### A Philosophy of Software Design
 - システムが複雑になるメカニズムと、複雑性がもたらす問題、それを解決するための方法について解説している
 - システムが複雑になるというのは、どういう状況を指しているのかの具体例が表記されていて、それを読むごとに、どこかで見たことあるわーみたいな共感があって面白い
 - 複雑性を理解すれば逆にシンプルな設計ができる的な本

<style>
h4 {
  color: #84b9cb;
  font-size: 16px !important;
}

ul {
  padding-left: 1rem;
  margin-top: 0.1rem;
}
li {
  @apply font-300;
  font-size:1.0rem;
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
layout: image-right
image: /screen_05.png
---

### Clean Craftsmanship
#### 規律、基準、倫理
- **規律**、**基準**、**倫理**の3つのレベルに分けて、プログラマー（and プログラマーのマネージャー）はどうあるべかのボブおじさんなりの哲学が書かれている
- デバッガーを今すぐ捨てろとか、完成しているコードにテストコードを書くからつまらないとか、企業がQAチームを設置しているのはプログラマーが仕事をしないからとか、過激な内容も記載されているが、実際は芯をくった内容だったりもして読んでていて面白い


<style>
h4 {
  color: #84b9cb;
  font-size: 16px !important;
}

ul {
  padding-left: 1rem;
  margin-top: 0.1rem;
}
li {
  @apply font-300;
  font-size:1.0rem;
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
layout: image-right
image: /screen_06.png
---

### 世界一流エンジニアの思考法 
- 米マイクロソフトで働く日本人エンジニアが著者
- 著者が一般的なエンジニアの視点で、米マイクロソフトシニアエンジニアと仕事して自身の思考回路の違いを実際にあったエピソードを交えて解説している
- 一般的には称賛されるような思考こそ、実は落とし穴がある的な本
- 読み物としても普通に面白い
- Audibleでも配信しているので手軽に聞ける


<style>
h4 {
  color: #84b9cb;
  font-size: 16px !important;
}

ul {
  padding-left: 1rem;
  margin-top: 0.1rem;
}
li {
  @apply font-300;
  font-size:1.0rem;
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
layout: image-right
image: /screen_08.png
---

### リファクタリング
#### 既存のコードを安全に改善する
 - 逆に一周してマーティン・ファウラーの名著を読んでみた
 - リファクタリングの基礎/哲学について解説している
 - リファクタリングの原初の本なので、このリファクタリングって、どんな効果があるの？みたいな疑問を持ったことがある人にオススメ
 - いろいろな技術書で名前が挙がることが多いので教養と一読しておくと解像度が上がるかも

<style>
h4 {
  color: #84b9cb;
  font-size: 16px !important;
}

ul {
  padding-left: 1rem;
  margin-top: 0.1rem;
}
li {
  @apply font-300;
  font-size:1.0rem;
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

# まとめ
 - OOUIを理解しているフロントエンドのコードのまとまり自体の認識が深まり変更に強いコードが書けるようになる
 - スクラム、DevOps、チームトポロジーを読むと開発のサイクルを回し続けるために必要になる要素を理解できる
 - A Philosophy of Software Designとリファクタリングは純粋にプログラミングとして勉強になる
 - Clean Craftsmanship、世界一流エンジニアの思考法は哲学的な視点もありメンタルモデルの構築に役に立つ
<style>
ul {
  padding-left: 1rem;
  margin-top: 0.1rem;
}
li {
  @apply font-300;
  font-size:1.0rem;
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
