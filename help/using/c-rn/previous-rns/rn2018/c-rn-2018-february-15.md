---
description: 2018年2月16日リリースのリリースノートです。
title: 2018 年 2 月 16 日
exl-id: 7276de37-c8cd-4e85-bc92-90c272e5bf94
translation-type: tm+mt
source-git-commit: a2449482e617939cfda7e367da34875bf187c4c9
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 5%

---

# 2018 年 2 月 15 日{#february}

2018年2月16日リリースのリリースノートです。

## 新機能 {#section_syx_mdt_wcb}

このリリースの実稼働版では、次の機能が新しく追加されました。

* **スマートタグ**

   Livefyreは、Adobe Senseiの画像認識技術を使用して、ライブラリに保存した画像に自動的にタグを付けます。
スマートタグを使用すると、コンテンツの検索とモデレートにかなりの時間を節約できます。 スマートタグを使用すると、次のことができます。

   * テキストだけでなく、画像のコンテンツに基づいて、保存した画像を正確に検索
   * テキストだけでなく、画像を分析する正確な検索用語に基づいて、ストリーム内のコンテンツを収集する

   スマートタグについて詳しくは、[スマートタグ](/help/using/c-features-livefyre/c-smart-tags/c-smart-tags.md#c_smart_tags)を参照してください。

* **製品内メッセージ。** Livefyre Studioにログインすると、お知らせウィンドウがポップアップ表示され、新機能に関する更新が表示されます。
* **カルーセルのUGC。** Livefyre Carousel AppでUGCコマースのすべての機能を使用できるようになりました。誘い文句（CTA：コールトゥアクション）ボタンを作成し、製品カタログをアプリに接続して、カルーセルから買い物かご体験を作成できます。

## タスク {#section_ehw_ndt_wcb}

次の表に示す問題は、このリリースで解決されました。

## 実稼働版リリース

| **問題のタイプ** | **コンポーネント** | **リリースノート** |
|---|---|---|
| 問題 | ModQ | 承認済みまたはトラッシュ済みとマークされたInstagram投稿がキューに再び入る問題を修正しました。 |
| 機能強化 | Rights Management | 権利要求を行う際に、期限切れのInstagramアカウントを使用しようとした場合に警告を表示する機能が強化されました。 |
| 問題 | トレンド | トレンドアプリで、HTTPSではなく、HTTPが許可される場合がある問題を修正しました。 |

## UATリリース

| **問題のタイプ** | **コンポーネント** | **リリースノート** |
|---|---|---|
| 機能強化 | Apps | Livefyreからアプリを削除する機能が追加されました。 |
| 問題 | 投票 | ポーリングでHTTPSのみを使用するように変更しました。 以前は、ポーリングはHTTPでの使用が許可されていました。 |
| 問題 | UGC | ビジュアライゼーションアプリのUGCが、製品IDで期待どおりにフィルターされなかった問題を修正しました。 |
