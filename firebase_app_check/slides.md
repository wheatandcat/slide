---
theme: ./theme
class: text-center
background:
highlighter: shiki
lineNumbers: false
info: |
  ## Firebase App Checkを実装したので紹介
drawings:
  persist: false
title: |
    Firebase App Checkを実装したので紹介
colorSchema: dark
fonts:
  sans: Noto Sans Japanese
  serif: Roboto Slab
  mono: Fira Code
---

### Firebase App Checkを実装したので紹介

<div class="flex justify-center pt-10">
  <img
    class="w-40 pt-2"
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

# Firebase App Check

 - [Firebase App Check](https://firebase.google.com/docs/app-check?hl=ja)
 - Firebase App Checkは、アプリが正当なものであることを確認して、不正なアクセスを防ぐためのFirebaseが提供しているセキュリティ機能
 - 各プラットフォームで保護を行うことができる
   - iOS
     - DeviceCheck
   - Android
     - Play Integrity
   - Web
     - reCAPTCHA v3


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

# DeviceCheck

 - [DeviceCheck](https://developer.apple.com/documentation/devicecheck)
 - Appleが提供するフレームワークで、Appleのサーバーと通信して端末情報を取得して不正なアクセスを防ぐのに使用されている
 - 各iOS端末でのアプリをインストール、アンインストールの情報をApple側で管理しており、フレームワークを使用して、その情報を元にトークンを生成、認証の仕組みを行うことができる
 - 正式にアプリをインストールした端末からしかトークンが発行できないので、クローリングやbotからのアクセスを防ぐことができる


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


# Play Integrity
 - [Play Integrity](https://developer.android.com/google/play/integrity?hl=ja)
 - Googleが提供するフレームワークで、Googleのサーバーと通信して端末情報を取得して不正なアクセスを防ぐのに使用されている
 - 基本的にはDeviceCheckのAndroid版
 - Play Integrityを使用することで、現在アクセスしているアプリがPlay Storeからインストールされたものか判別できる
 - AndroidはiOSよりも簡単に野良アプリをインストール可能なので、そういったアプリからのアクセスを防ぐことができる


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

# Firebase App Checkの機能

 - 以下のリソースに対して保護を行うことができる
   - 各Firebaseのリソース
     - Storage
     - Functions
     - Firestore
     - Authentication
     - etc
       - **※モニタリングの情報をDEMOで表示** 
   - Firebase以外のリソースの場合は実装すれば保護が可能
     - [カスタム バックエンドから App Check トークンを検証する](https://firebase.google.com/docs/app-check/custom-resource-backend?hl=ja&authuser=0)
     


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

# Firebase App Checkのデバッグトークン①

<div class="flex justify-center pb-10">
  <img
    class="w-120 mt-2 border border-white border-opacity-20"
    src="/screen_01.png"
  />
</div>

 - App Checkを実装するとストアからインストールされたアプリしかアクセスできなくなるので、そのままだと開発時にアクセスできなくなってしまう
 - そのため、開発時はデバッグトークンを使用してアクセスできるようにする



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

# Firebase App Checkのデバッグトークン②


```dart
await FirebaseAppCheck.instance.activate(
    androidProvider:
        kReleaseMode ? AndroidProvider.playIntegrity : AndroidProvider.debug,
    appleProvider:
        kReleaseMode ? AppleProvider.deviceCheck : AppleProvider.debug,
  );
```

<br/>

 - デバッグトークンはProviderを**debug**にすることで有効になる
 - アプリを起動するとデバッグトークンが発行されて、コンソールに設定するとアクセスが可能になる
 - ※デバッグトークンの表示は以下を参考
   - [FlutterでFirebase App Checkに対応（+Firebase App Distributionで配信時の対応）](https://www.wheatandcat.me/entry/2024/11/02/173649)



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

# App Checkの実装①

 - 実装環境
   - アプリ: Flutter
   - バックエンド: NestJS
 - 事前準備
   - DeviceCheckの導入
     - 参考:[【Flutter】App Check を導入して Firebase を守ろう！(DeviceCheck)](https://zenn.dev/susatthi/articles/20230316-172748-flutter-firebase-app-check#ios-(-devicecheck-))
   - Play Integrityの導入
     - 参考:[【Flutter】App Check を導入して Firebase を守ろう！(Play Integrity)](https://zenn.dev/susatthi/articles/20230316-172748-flutter-firebase-app-check#android-(-play-integrity-)-%E3%81%AE%E5%B0%8E%E5%85%A5%E6%89%8B%E9%A0%86)

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

# App Checkの実装②

 - PR
   - [Firebase App Check実装](https://github.com/wheatandcat/stock-keeper/pull/67)
 - backendの実装
   - [対象コード](https://github.com/wheatandcat/stock-keeper/blob/9a96dab7f1135c0bb5e9c6ca285ceac1c9e0f920/typescript/backend/src/common/guards/auth/auth.guard.ts#L32-L42)
 - アプリの実装
   - [対象コード1](https://github.com/wheatandcat/stock-keeper/blob/eee3db7b1b2f019a59e5647326c7c5c7e790fe2e/dart/app/lib/utils/graphql.dart#L26)
   - [対象コード2](https://github.com/wheatandcat/stock-keeper/blob/eee3db7b1b2f019a59e5647326c7c5c7e790fe2e/dart/app/lib/utils/graphql.dart#L89-L96)
    
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

# App Checkの実装③

<br/>

App Checkを実装した状態でトークンなしでAPIにアクセスするとエラーが発生してアクセスできない

<div class="flex justify-center pb-10">
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
  - Firebase App Checkを導入することで不正アクセスを防ぐことができる
  - 開発時はデバッグトークンを使用してアクセスできる
  - デバッグトークンはアプリを再インストールする毎に変更されるので、その度にコンソールに設定する必要があるので複数人開発では運用を考える必要がある
  - [Firebase App Distribution](https://firebase.google.com/docs/app-distribution?hl=ja)を使って配信した場合に、Androidだと**Play Integrity**でエラーにされてしまうので注意（今回の開発だとAndroid側は本番以外はデバッグトークンを使用して認証させた）


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
