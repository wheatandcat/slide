---
theme: ./theme
class: text-center
background:
highlighter: shiki
lineNumbers: false
info: |
  ##  ユニバーサルリンク/アプリリンクを使ってQRコードでゲストログインできるようにする
drawings:
  persist: false
title: |
   ユニバーサルリンク/アプリリンクを使ってQRコードでゲストログインできるようにする
colorSchema: dark
fonts:
  sans: Noto Sans Japanese
  serif: Roboto Slab
  mono: Fira Code
---

### ユニバーサルリンク/アプリリンクを使って<br/>QRコードでゲストログインできるようにする

<div class="flex justify-center pt-10">
  <img
    class="w-40 pt-2"
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

# 実装した機能の概要

- 以下のissueで実装
  - [QRコードでユーザーを招待できるようにする](https://github.com/wheatandcat/stock-keeper/issues/29)
- 概要
  - ログインしているユーザーが招待用のQRコードを生成
  - QRコードを読み取ると、招待したユーザーがゲストログインできる
 - モチベーション
   - アプリの使用にはアカウント作成が必要
   - アプリ的に家族と共有して使用したいユースケースが多い
   - その際にアカウント作成を求めるのはハードルが高いので、QRコードでゲストログインできるようにしたい
   - QRコードの読み取りはアプリ内、アプリ外どちらでも可能にしたい

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


# 実装に必要な技術
 - backend/アプリのゲストログインの実装
 - QRコード作成/スキャン
 - QRコードをスキャンした時にアプリに指定の動作をさせる


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


# 実装に必要な技術
 - backend/アプリのゲストログインの実装
   - ゲストユーザーログインのトークンを発行してHeaderに設定して認証するミドルウェアを実装
 - QRコード作成/スキャン
   - QRコード作成: [qr_flutter](https://pub.dev/packages/qr_flutter)
   - QRコードスキャン: [mobile_scanner](https://pub.dev/packages/mobile_scanner)
 - QRコードをスキャンした時にアプリに指定の動作をさせる
   - iOS: [ユニバーサルリンク](https://developer.apple.com/ios/universal-links/)
   - Android: [アプリリンク](https://developer.android.com/training/app-links?hl=ja)
   - 上記のリンクからアプリを起動するためのURLスキーム設定: [go_router](https://pub.dev/packages/go_router)

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

# ユニバーサルリンクとは

 - Webサイトのリンクをクリックした時にiOSのアプリを起動させる仕組み
 - Appleデバイス専用のディープリンクのためのプロトコル
 - アプリを起動時にパラメータを付与することができるので、それを利用して特定の画面に遷移させることができる
 - iOS 9以降で利用可能


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

# ユニバーサルリンクの実装①

<img
  class="pt-2 w-140"
  src="/screen_01.png"
/>

 - XCodeでアプリを開いて、CapabilitiesのAssociated Domainsを追加
 - Associated Domainsに`applinks:****.com`を追加

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

# ユニバーサルリンクの実装②

 - 先ほどのapplinksに設定をしたドメインの`.well-known/apple-app-site-association`で以下のjsonを設定
  - ```json
    {
      "applinks": {
        "apps": [],
        "details": [
          {
            "appID": "7KWTGL2ZDY.com.unicorn.stockkeeper",
            "paths": ["/"]
          }
        ]
      }
    }
    ```
  - `appID`は`Apple Developerのteam id`と`bundle id`を組み合わせたものを指定
  - これでiOS端末から`https://stock-keeper-review.web.app`を開いた時に、アプリがインストール済みの場合にアプリが起動できる

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

# アプリリンクとは

 - 先ほど説明したユニバーサルリンクのAndroid版
 - Android 6.0以降で対応


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

# アプリリンクの実装①

AndroidManifest.xmlに以下を追加

```xml{all|5}
<intent-filter android:autoVerify="true">
  <action android:name="android.intent.action.VIEW" />
  <category android:name="android.intent.category.DEFAULT" />
  <category android:name="android.intent.category.BROWSABLE" />
  <data android:scheme="http" android:host="stock-keeper-review.web.app" />
  <data android:scheme="https" />
</intent-filter>
```

`android:host` にアプリに遷移させたいドメインを指定


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

# アプリリンクの実装②

 - 先ほどの`android:host`に設定をしたドメインの`.well-known/assetlinks.json`で以下のjsonを設定
  - ```json
    [
      {
        "relation": ["delegate_permission/common.handle_all_urls"],
        "target": {
          "namespace": "android_app",
          "package_name": "com.unicorn.stockkeeper",
          "sha256_cert_fingerprints": [
            "B7:FA:3A:2D:DA:29:22:6B:FF:02:40:55:69:E8:6D:8D:54:40:89:CE:69:8C:E6:E3:7C:FF:1B:9B:8E:82:EF:A8"
          ]
        }
      }
    ]
    ```
  - `sha256_cert_fingerprints`は`アプリの署名証明書`のSHA-256ハッシュ値を指定
  - これでAndroid端末から`https://stock-keeper-review.web.app`を開いた時に、アプリがインストール済みの場合にアプリが起動できる


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

# go_routerでURLスキーマを定義

以下のようにgo_routerでURLスキーマを定義


```dart{all|12|11-18}
final goRouter = GoRouter(
  initialLocation: '/',
  routes: [
    GoRoute(
        path: '/',
        name: "home",
        pageBuilder: (context, state) {
          return MaterialPage(key: state.pageKey, child: const AuthWrapper());
        },
        routes: [
          GoRoute(
            path: "guest/login/:code",
            name: "guest_login",
            pageBuilder: (context, state) {
              final code = state.pathParameters['code']!;
              return BottomSheetPage(builder: (_) => ShareBottomSheet(code: code));
            },
          ),
```

`https://stock-keeper-review.web.app/guest/login/xxxxxx`のURLでゲストログインが可能



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
  color: #fff !important;
  opacity: 1 !important;
}
</style>



---
layout: default
---

# 動作検証

 - [QRコードに招待URLを設定](https://github.com/wheatandcat/stock-keeper/pull/65)
 - ※PRにアプリ内でQRコードを読み取るデモと、アプリ外でQRコードを読み取るデモの動画を貼っている


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

# まとめ
  - ユニバーサルリンク/アプリリンクを使ってQRコードでゲストログインを作ることができた
  - 設定箇所さえ分かれば、実装はそれほど難しくない
  - ゲストの認証がHeaderに設定されたトークンのみ行っていてセキュリティ的には問題がある
  - なので、この後[Firebase App Check](https://firebase.google.com/docs/app-check?hl=ja)を導入して端末以外からのアクセスを制限してカバーして機能完成予定

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
