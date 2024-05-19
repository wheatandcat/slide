---
theme: ./theme
class: text-center
background:
highlighter: shiki
lineNumbers: false
info: |
  ##  Flutter HooksとRiverpodの解説
drawings:
  persist: false
title: |
   Flutter HooksとRiverpodの解説
colorSchema: dark
fonts:
  sans: Noto Sans Japanese
  serif: Roboto Slab
  mono: Fira Code
---

### Flutter HooksとRiverpodの解説

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

# Flutterとは

- Google開発のオープンソースのマルチプラットフォームの開発フレームワーク
- 一つのコードベースから、**iOS、Android、Web、Windows、Mac、Linuxアプリ**など複数のプラットフォームの作成が可能
- 言語は**Dart**を使用
- Google独自のUI Widgetを使用（Material Designベース）


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

# Flutter Hooksとは
  - React HooksのFlutter版
    - [flutter_hooks](https://pub.dev/packages/flutter_hooks)
  - コンポーネントの状態を管理するためのライブラリ
  - Flutter標準の**Stateful Widget**のコードを簡潔に書くことができる

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
layout: two-cols
---

# StatefulWidgetの例

 - ①. StatefulWidget継承したクラスを宣言
 - ②. Stateクラスを宣言
 - ③. Stateの初期化
 - ④. Stateの更新
 - ⑤. Stateの参照

::right::

```dart{all|1-4|6-22|7|12-16|17}
class Count extends StatefulWidget {
  @override
  State<Count> createState() => _CountState();
}

class _CountState extends State<Count> {
  int _counter = 0;

  @override
  Widget build(BuildContext context) {
    return TextButton(
      onPressed: () => {
        setState(() {
          _counter++;
        }),
      },
      child: Text('Increment: $_counter'),
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
layout: two-cols
---

# Flutter Hooksの例

 - ①. HookWidgetを継承したクラスを宣言
 - ②. Stateの初期化
 - ③. Stateの更新
 - ④. Stateの参照

::right::

```dart{all|4|6|7}
class Count extends HookWidget {
  @override
  Widget build(BuildContext context) {
    final count = useState(0);
    return TextButton(
        onPressed: () => count.value++,
        child: Text('Increment: ${count.value}'),
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

# useEffectの解説

  - Widgetのライフサイクルで処理をさせたい時にuseEffectを使ってみる
    - 生成時、破棄時、更新時
  - 概念的にはReactの[useEffect](https://ja.react.dev/reference/react/useEffect#connecting-to-an-external-system)と同じ   


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

# useEffectの例

```dart{all|3-7|9-12|13-18}
final id = useState<int>(0);

useEffect(() {
  // ①. idが変更されたら実行
  getItems(id.value);
}, [id.value]);

useEffect(() {
  // ②. 初回のみ実行
    debugPrint('初回のみ実行');
}, const []);

useEffect(() {
  // ③. 破棄時に実行
  return () => {
    debugPrint('破棄時に実行');
  };
}, [id.value]);
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

# Custom Hookの例

 - コード量が多くなってくると状態管理とViewのコードを分割したくなる
 - その時にCustom Hookを使うと便利
 - コードの例は以下を参照
   - [コードのURL](https://github.com/wheatandcat/stock-keeper/blob/dabbcee31980fea1da90356062409494ba85eff2/lib/features/category/hooks/useItems.dart#L1-L47)
 - 差分は以下の通り
   - [差分のURL](https://github.com/wheatandcat/stock-keeper/pull/16/commits/dabbcee31980fea1da90356062409494ba85eff2)


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

# Riverpodとは

  - [Riverpod](https://riverpod.dev/)
  - グローバルな状態管理をしたい時に使うライブラリ
  - Reactでいうところの[Context API](https://ja.react.dev/learn/passing-data-deeply-with-context)のようなもの
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
layout: two-cols
---

# Riverpodの例

 - ①. Providerを宣言
 - ②. Providerを取得
 - ③. Providerの値を参照
 - ④. Providerの値を更新
 - [Demo用のURL](https://dartpad.dev/?id=47a5ea4b703dae053d45d76696a20bc5)
    

::right::

■ lib/providers/counter.dart
```dart
final countProvider = StateProvider((ref) => 0);
```

■ lib/main.dart
```dart{all|4|9|11}
class HomePage extends ConsumerWidget {
  @override
  Widget build(BuildContext context, WidgetRef ref) {
    final count = ref.watch(countProvider);

    return Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: <Widget>[
            Text('$count'),
            FloatingActionButton(
              onPressed: () => ref.read(countProvider.notifier).state++,
              child: Icon(Icons.add),
            ),
          ],
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

## まとめ

 - Flutterの状態管理で**Flutter Hooks**と**Riverpod**を触ってみたが、思っていた以上にReactと同じ方式だったので、Reactの知識があればすぐに使える
 - Flutterがクラスベースで作成されている言語なのに、Hooksが関数ベースで作成されているのが、若干ちぐはぐな感じはしている
 - ただ、[riverpod_generator](https://pub.dev/packages/riverpod_generator)のようなRiverpodの宣言自体を自動生成できる部分はReactよりも進んでいるかも
   - Providerの宣言の種類が多すぎるのでコード生成すると楽
   - [各Providerの役割と使い分け｜Flutter x Riverpod でアプリ開発！実践入門](https://zenn.dev/riscait/books/flutter-riverpod-practical-introduction/viewer/how-to-choose-a-provider)

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
