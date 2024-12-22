---
theme: ./theme
class: text-center
background:
highlighter: shiki
lineNumbers: false
info: |
  ## FlutterでOCRを活用した商品情報の取得を実装してみた
drawings:
  persist: false
title: |
    FlutterでOCRを活用した商品情報の取得を実装してみた
colorSchema: dark
fonts:
  sans: Noto Sans Japanese
  serif: Roboto Slab
  mono: Fira Code
---

### FlutterでOCRを活用した商品情報の取得を実装してみた

<div class="flex justify-center pt-10">
  <img
    class="w-15 pt-2"
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

# OCR

- 光学式文字認識（Optical Character Recognition）の略
- 画像から文字を認識してテキストに変換する技術 


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

# モチベーション

 - 在庫管理アプリを作成中で、なるべく手間を省いて在庫商品を登録できるようにしたい
 - 初めに実装したのはバーコードを読み込んで商品を登録する方式
 - しかし、実際に運用してみると以下のケースがあることが分かった
   - バーコードから商品情報を取得できないケースがある
   - バーコードが外箱に記載されており、商品のみ手元にある
 - 上記の課題を解決するために**OCR**を活用し、画像から商品情報を取得する方法を試した。


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


# 使用するライブラリ & サービス
 - [google_mlkit_text_recognition](https://pub.dev/packages/google_mlkit_text_recognition)
   - 画像から文字列を抽出
 - [Cloud Natural Language | Google Cloud](https://cloud.google.com/natural-language)
   - OCRで取得したテキストから商品名を抽出
 - [Yahoo!ショッピングAPI](https://developer.yahoo.co.jp/webapi/shopping/v3/itemsearch.html)
   - 抽出したキーワードで商品情報を取得

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

# 実装

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

# OCRで画像から文字を抽出①

```dart {all|1,4-8|9-12}
import 'package:google_mlkit_text_recognition/google_mlkit_text_recognition.dart';
import 'dart:io';

Future<List<String>> imageTextRecognizer(File image) async { 
  final inputImage = InputImage.fromFile(image);
  final textRecognizer = TextRecognizer(script: TextRecognitionScript.japanese);
  final RecognizedText recognizedText =
      await textRecognizer.processImage(inputImage);
  final texts = recognizedText.blocks
      .map((block) => block.text.replaceAll('\n', ' '))
      .where((text) => text.length > 1 && !RegExp(r'^\d+$').hasMatch(text))
      .toList();

  return texts;
}
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
layout: image-right
image: ./screen_01.jpg
---
# 文字を抽出②

右の画像を読み込むと以下のテキストが抽出できる

```json {all|6,8|10,11}
[
  "38%",
  "\\売上/",
  "No.",
  "※インテージSRI+",
  "一般用ウェッ外ティッシ",
  "累計販売金額",
  "207年\\月20B",
  "▲ここまで引っぱってご使用ください。",
  "シルコット",
  "ウェットティッシュ",
  "、純水99%",
  "手·口まわりの汚れに",
  "メイク時の手指の拭き取りに デ",
  "コアウォーター",
  "ノンアルコール"
]
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

# 抽出文字列から商品名を特定①

Google Cloud Natural Languageの「エンティティ分析」を使ってテキストを解析 <br/>
商品名を自動抽出する

[エンティティ分析可能なType](https://cloud.google.com/natural-language/docs/reference/rest/v2/Entity#Type)

```ts
import { LanguageServiceClient } from '@google-cloud/language'

export const analyzeText = async (text: string) => {
  const client = new LanguageServiceClient()

  const document = {
    content: text,
    type: 'PLAIN_TEXT' as const,
  }

  const [result] = await client.analyzeEntities({ document })
  const { entities } = result

  const entityList = entities.filter(
    (entity) => entity.type === 'CONSUMER_GOOD'
  )

  省略...
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

# 抽出文字列から商品名を特定①

抽出結果は以下の通り、この情報を元に商品名を特定する

```json {all|11}
[
  "38%", → UNKNOWN
  "\\売上/", → UNKNOWN
  "No.", → UNKNOWN
  "※インテージSRI+", → UNKNOWN
  "一般用ウェッ外ティッシ", → UNKNOWN
  "累計販売金額", → UNKNOWN
  "207年\\月20B", → UNKNOWN
  "▲ここまで引っぱってご使用ください。", → UNKNOWN
  "シルコット", → UNKNOWN
  "ウェットティッシュ", → CONSUMER_GOOD
  "、純水99%", → UNKNOWN
  "手·口まわりの汚れに", → UNKNOWN
  "メイク時の手指の拭き取りに デ",
  "コアウォーター", → UNKNOWN
  "ノンアルコール" → UNKNOWN
]
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

# 商品検索の自動取得①

先ほど抽出した商品名を[Yahoo!ショッピングAPI](https://developer.yahoo.co.jp/webapi/shopping/v3/itemsearch.html)で検索して商品情報を取得<br/>
ヒット商品の中から、**商品名以外のキーワードが一致する商品以外をフィルタリングする**


<div class="flex justify-center pb-10 w-150">
  <img
    class="mt-2 border border-white border-opacity-20"
    src="/screen_02.png"
  />
</div>

<style>
ul {
  padding-left: 1rem;
  margin-top: 0.1rem;
}
li {
  @apply font-300;
  font-size:1.1rem;
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
image: ./screen_03.png
---
# 商品検索の自動取得②

<br/>

取得できた商品情報を表示させて、ユーザーに選択させるUIを表示させる

自動検索で商品が取得できなかった場合のために、手動検索の機能も用意している

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

# 商品の手動検索機能

- 1.「テキストで検索」ボタンを押下
- 2.抽出されたテキスト一覧から商品名を選択または修正
- 3.検索ボタンをタッチ


<div class="flex justify-center">
  <img
    class="mt-2 border border-white border-opacity-20"
    src="/screen_04.png"
  />
</div>

<style>
ul {
  padding-left: 1rem;
  margin-top: 0.1rem;
}
li {
  @apply font-300;
  font-size:1.1rem;
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

## [動画](https://youtu.be/-braelw-sOI)

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
- 今回の仕組みの実装で、8-9割の商品情報を自動取得できるようになった
- 実際に運用してみて以下の課題もあるので
  - フォントやデザインの影響でOCRの精度が低下する場合がある
  - ショッピングAPIでヒットしない商品がある
- OCR + AIの可能性は工夫次第で、色々活用できそう

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
