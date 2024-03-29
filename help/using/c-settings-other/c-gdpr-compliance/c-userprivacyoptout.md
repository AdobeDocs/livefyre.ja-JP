---
description: サイトの訪問者追加がこの追跡を許可するために、userPrivacyOptOutフラグをページにオプトアウト設定します。
title: userPrivacyOptOut
exl-id: 1e935e69-60af-4151-905c-93a1cccbeb49
translation-type: tm+mt
source-git-commit: a2449482e617939cfda7e367da34875bf187c4c9
workflow-type: tm+mt
source-wordcount: '208'
ht-degree: 0%

---

# userPrivacyOptOut{#userprivacyoptout}

サイト訪問者追加がこのトラッキングを行えるように、ページオプトアウトの`userPrivacyOptOut`フラグ。

Livefyreは、Livefyre Appsでユーザーのアクティビティを追跡するJavaScriptイベントを提供しています。

Livefyreアプリを埋め込んだ場合、訪問者が追跡に同意しないと、訪問者のプライバシーを守るためにLivefyreの機能を無効にするように動的に設定できます。

設定時にLivefyreは次の操作を行います。

* アプリで認証サポートを無効にします。
* Livecountとイベントの生成の無効化
* ページ上の任意のアプリで作成された既存のcookieを削除する
* サードパーティのドメインの画像を使用したプロキシメディア。サードパーティがcookieを作成できないようにするために使用します。
* 追加のクリックによる表示が必要なサードパーティビデオに対するビデオマスクのクリックスルーの有効化

## ページのオプトアウト設定

Livefyreアプリを埋め込む統合では、サイト訪問者が1つのJavaScript変数を使用して同意を与えていない場合に、Livefyreを設定できます。

説明:

1. 追加`Livefyre.js` JavaScriptの前のページの`userPrivacyOptOut`フラグ：

   ```
   window.Livefyre = {userPrivacyOptOut: true};
   ```

1. 追加`Livefyre.js`を`userPrivacyOptOut`の後の任意の場所に移動します。

   管理者のプライバシー設定を使用してLivefyreアプリがインスタンス化されます。

   >[!NOTE]
   >
   >Livefyre Appsが読み込まれた後は、`userPrivacyOptOut`の値を変更しないでください。

サイトの訪問者が選択した場合、同意ワークフローで`userPrivacyOptOut`がtrueに設定されていることを確認オプトアウトします。
