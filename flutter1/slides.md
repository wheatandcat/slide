---
theme: ./theme
class: text-center
background:
highlighter: shiki
lineNumbers: false
info: |
  ## Flutter × GraphQLでアプリを作ってみる
drawings:
  persist: false
title: |
  Flutter × GraphQLでアプリを作ってみる
colorSchema: dark
fonts:
  sans: Noto Sans Japanese
  serif: Roboto Slab
  mono: Fira Code
---

### Flutter × GraphQLでアプリを作ってみる

<div class="flex justify-center pt-10">
  <img
    class="w-120 pt-2"
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

# Flutterとは？

- Google開発のオープンソースのマルチプラットフォームの開発フレームワーク
- 一つのコードベースから、**iOS、Android、Web、Windows、Mac、Linuxアプリ**など複数のプラットフォームの作成が可能
- 言語は**Dart**を使用
- Google独自のUI Widgetを使用（Material Designベース）
  - なので、プラットフォーム毎でUIに差分が発生しづらい


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

# 今回の開発物

<div class="flex justify-center pb-6">
  <img
    class="w-90 pt-2"
    src="/screen_01.png"
  />
</div>

- まだ開発中だが、家の在庫を管理するアプリを作成中
- 上記の画像のような画面構成にする予定




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

# 現在の開発構成

- Frontend
  - [Flutter](https://flutter.dev/)
- Backend
  - [NestJS](https://nestjs.com/)
  - [Prisma](https://www.prisma.io/)
  - [PlanetScale](https://planetscale.com/)
  - [GraphQL Code Generator](https://the-guild.dev/graphql/codegen)
  - [Cloud Run](https://cloud.google.com/run?hl=ja)

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

# 開発構成のモチベーション

- 普段はReact Nativeでアプリ開発をしているので、よく比較対象に挙がる **Flutter** で本格的な開発をしてみたかった
- NestJSの採用の一番大きい理由は、**Prisma**を使って開発をしたかったから
  - 前に試した[T3 Stack](https://create.t3.gg/)での開発体験が良かったので、他の構成でも使ってみたかった
  - [tRPC](https://trpc.io/)が、もっとも望ましかったが、Flutterではサポートされていないので、**GraphQL**を採用
- NestJSは**BFF**の構成にした場合に、採用されるけーすが多いので、触ってみたかった
- Flutterでも[graphql_codegen](https://pub.dev/documentation/graphql_codegen/latest/)で型安全で実装はできるので、それを使って開発
- 各比較についてはスライドの最後に記載

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

# Flutterの開発

基本的なコードの書き方は以下のような感じ

```dart {all|3-6|7-24|14-16|17-19|all}
import 'package:flutter/material.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        appBar: AppBar(
          title: Text('Hello Flutter'),
        ),
        body: Center(
          child: Text('Welcome to Flutter'),
        ),
      ),
    );
  }
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
layout: default
---

# Widgetとは？

 - 先程のコードで説明した通り、Flutterでは**Widget**を使用してUIを構築していく
 - FlutterではWidgetを公式から提供されており、それらを組み合わせて画面を作成していく
 - 提供されているWidgetの一覧は以下のページから確認可能
   - [Widget catalog | Flutter](https://flutter.dev/docs/development/ui/widgets)

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

# FlutterとGraphQLの連携①

Flutterでも[graphql_codegen](https://pub.dev/documentation/graphql_codegen/latest/)を導入すれば型安全でGraphQLのクエリを実行できるので手順を紹介

まずは、backendからGraphQLのスキーマファイルを取得

```graphql {all}
type Query {
  categories: [Category]
  category(id: Int!): Category
}
type Category {
  "カテゴリーID"
  id: ID!
  "カテゴリー名"
  name: String!
  "順番"
  order: Int!
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
layout: default
---

# FlutterとGraphQLの連携②

次にFlutterからアクセスするためのクエリを作成

```graphql {all}
query Category($id: Int!) {
  category(id: $id) {
    id
    name
    order
  }
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
layout: default
---

# FlutterとGraphQLの連携③

[graphql_codegen](https://pub.dev/documentation/graphql_codegen/latest/)の初期設定をして以下のコマンドを実行

```bash
dart run build_runner build
```

以下のファイルが生成される
 - [lib/graphql/category.gql.dart](https://github.com/wheatandcat/stock-keeper/blob/2301e94bdc4f7e5afa8889aa2d7eae9cad32eb91/lib/graphql/category.gql.dart)

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

# FlutterとGraphQLの連携④

③で生成したファイルを参照して、以下のようにクエリを実行して値を取得

```dart {all|8-9|13-15|17-20|all}
class Items extends HookWidget {
  final int id;

  const Items({super.key, required this.id});

  @override
  Widget build(BuildContext context) {
    final queryResult = useQuery$Category(
        Options$Query$Category(variables: Variables$Query$Category(id: id)));

    final result = queryResult.result;

    if (result.isLoading) {
      return const Text('Loading...');
    }

    final Query$Category$category category = Query$Category$category.fromJson(
        result.data!['category'] as Map<String, dynamic>);

    return Text(category.name);
  }
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
layout: default
---

# 今回作成したリポジトリの紹介

 - Repository
   - [wheatandcat/stock-keeper](https://github.com/wheatandcat/stock-keeper)
   - [wheatandcat/stock-keeper-backend](https://github.com/wheatandcat/stock-keeper-backend)


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
  color: #fff;
  opacity: 1;
}
</style>


---

## React Nativeとの比較


まだ、Flutterの方はざっくりな開発しかしていないが、現状の所感での比較を記載
  - パフォーマンスチューニングのやりやすさ
    - Flutter >> React Native
  - 運用/保守コスト
    - Flutter >> React Native 
  - UI/システムの柔軟性
    - React Native > Flutter
  - 開発のとっつきやすさ
    - Expo >>> Flutter > React Native
  - エコシステムの充実度/熟練度
    - React Native >>> Flutter
  - backendとの連携
    - React Native > Flutter

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

## まとめ

 - よくFlutterとReact Nativeの比較がされる記事を見かけていたが、Flutterは触ってなかったので、あまりピンと来てなかったが、今回の開発でその辺が把握できた
 - dartは簡単なので、たぶんReact経験者なら、すぐに慣れると思う 
 - Flutterの魅力はGoogle独自のWidgetを使用することで、プラットフォーム毎でUIに差分が発生しづらく保守コストが少なく済むところ
 - React Nativeはパフォーマンスチューニングのコーディング難易度が非常に高いので、その辺はFlutterの方が強そう
 - エコシステムの充実度はnpmの圧倒的な数 & 完成度の高いパッケージが多いので、この辺はReact Nativeの方に軍配が上がる
 - GraphQLの連携周りも React Nativeの方がサポートが充実している
 - 初期開発の充実度は[Expo](https://expo.dev/)が最も優れており、アプリリリースまではコストは一番低そう
 - 今後増えてくる[tRPC](https://trpc.io/)のサポートに関してはFultterだと言語の壁があり、もしサポートされてもファースト扱いにはならないので、この辺はReact Nativeの方が有利そう
 - 思った以上に良い勝負をしているので、今後の動向が楽しみ 

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
