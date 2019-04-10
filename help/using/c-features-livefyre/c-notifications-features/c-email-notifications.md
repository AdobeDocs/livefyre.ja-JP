---
description: ユーザーが通知頻度とコンテンツを選択できるようにします。
seo-description: ユーザーが通知頻度とコンテンツを選択できるようにします。
seo-title: 電子メール通知
solution: Experience Manager
title: 電子メール通知
uuid: 27dank133- bd8d-4949-8146-1254c160d3af
translation-type: tm+mt
source-git-commit: 566ea2587f101202045488e9f4edf73ece100293

---


# 電子メール通知{#email-notifications}

ユーザーが通知頻度とコンテンツを選択できるようにします。

**ユーザーおよびモデレーターに対して電子メール通知を有効にします。**

Livefyreアプリでは、特定のアクションに基づいて、ユーザーおよびモデレーターに対して電子メール通知を有効にすることができます。通知は、コンテンツがストリームに投稿される時間に基づいているので、ユーザーは関心のある会話でアクションを実行したり、コメントの1つに対して「いいね!"をしたり返信したりしたときに通知を受けることができます。

ユーザーおよびモデレーターは電子メール通知をオプトインまたはオプトアウトし、電子メール受信頻度を設定できます。ここでは、電子メール通知を設定およびカスタマイズする方法について説明します。

* ユーザー電子メールオプション:使用可能なユーザー通知オプションを使用できます。
* モデレーターの電子メールオプション:使用可能なモデレーター通知オプションを使用できます。
* Livefyre Identity Email Options:Livefyre IDの一部として送信される電子メール。これらの電子メールはLivefyre ID顧客にのみ関連しています。
* Livefyreとのデータ同期:環境設定のLivefyreとの同期を維持しています。
* 電子メールのカスタマイズ:使用可能な電子メールのカスタマイズ

**設定/統合設定/電子メール通知設定** オプションを使用して、ネットワークの電子メール通知をカスタマイズします。

>[!NOTE]
>
>エンドユーザーが意図しないメールを受信しないようにするには、Livefyre UAT環境から電子メール通知を送信しません。

**ユーザー電子メールオプション**

Livefyreでは、ユーザーがサイトアクティビティの電子メール通知を受信できます。Livefyreが提供するユーザープロファイルの統合設定を使用して、ユーザーが通知スケジュール用の環境設定を選択できるようにします。

>[!NOTE]
>
>電子メールは、SocialSyncから取得されたコンテンツではなく、手動でストリームに投稿されたコンテンツに対してのみ送信されます。

ユーザーが通知の環境設定を設定できるようにするには、ユーザープロファイルシステムのユーザー設定に「電子メール通知」セクションを含めます。対応するフィールドをユーザープロファイルデータベーススキーマに追加し、Ping for Pullを使用してユーザー設定を管理します。（ネットワークのデフォルトの周波数を定義するには、テクニカルインテグレーションマネージャーにご相談ください。Enterprise Profilesのお客様の場合、選択したデフォルトをLivefyreの配信チームに渡して、Livefyreデータベースの設定を行います。）

サイトのユーザーは、会話に従って、コメントエディターの **[!UICONTROL +Follow]** ボタンをクリックして電子メール通知を受信することができます。通知の環境設定はLivefyreネットワークレベルで定義されます。ユーザー設定は、ネットワーク全体のすべてのサイトおよび会話に適用されます。

**推奨デフォルト**

* 次に示す会話でユーザーがコメントします。**時間別ダイジェスト**
* 誰かが自分のコメントの1つに気に入ったものです。**時間別ダイジェスト**
* 誰かが自分のコメントの1つに返信します。**すぐ****
* コメントを終了したら、会話を自動フォローします。** off**（checked）

**注意**:電子メール通知は、時間コンテンツが承認され、ストリームに含めることができます。

Livefyreには、次の2つの電子メール頻度オプションがあります。

* すぐに
* 時間別ダイジェスト

**すぐに**

電子メールには、投稿のテキスト、記事のタイトル、発言者のユーザー名、 **およびそのページ上のコンテンツにユーザーが移動する返信** リンクが即座に表示されます。これらの電子メールには、フッターに **登録解除** リンクが含まれているので、ユーザーはそのコレクションに対する電子メール通知の登録を解除できます。"** unsubscriber**"をクリックすると、コレクションから登録解除されたことを確認できる確認ページが表示されます。

**時間別ダイジェスト**

時間別ダイジェストで送信される電子メールには、すべてのコンテンツ、コンテンツへの返信、およびユーザーがフォローしているアプリごとの「いいね!"の最後の時間（その他）のコンテンツが表示されます。ユーザーがネットワーク全体で複数のアプリをフォローしている場合、各アプリのダイジェスト電子メールが1つずつ受信されます。

>[!NOTE]
>
>新しいコンテンツを使用しない会話の場合、時間別ダイジェストを有効にしたユーザーは、新しいコンテンツ投稿の直後に通知を受け取ります。

**モデレーターの電子メールオプション**

モデレーターは、フォローされているアプリに投稿されたコンテンツの電子メールを受信したり、コメントについて、モデレートしているアプリにスパムや不快さをフラグ付けしたりできます。**注意:** これらのカテゴリはモデレーター通知で重要と見なされないので、ユーザーが「同意しない」または「トピック外」というコメントにフラグを付けた場合、電子メールは送信されません。

モデレーター_コメントおよびモデレーター_ flagsフィールドをモデレーターユーザープロファイル設定のページデータベーススキーマに追加して、モデレーターが電子メール通知の頻度を更新できるようにし、必要に応じてオプトアウトします。Livefyreでは、これら2つのモデレーターの電子メール通知フィールドを **無関係**に設定することをお勧めします。オプションには、常に **（** デフォルト）、 **即時**および **頻繁**に指定できます。

**モデレーター電子メール（フラグ付きコンテンツ）:**

モデレートされたアプリでコンテンツがフラグ付けされると、モデレーターに送信される電子メールには、フラグ付きのコンテンツ、コンテンツにフラグを付けたユーザー、およびコンテンツページに戻るリンクが表示されます。

ユーザーがプロファイルシステムで自分のサイトの電子メール通知の環境設定を変更したら、LivefyreのPingを使用してLivefyreリモートプロファイルシステムにアップデートを同期します。

**Livefyreとのデータ同期**

## 電子メールのカスタマイズ {#section_jxb_c5k_yy}

電子メール通知テンプレート内のいくつかのフィールドは、スタイルやブランドに合わせて変更できます。

* **[!UICONTROL From Email Address]**

   すべての電子メール通知について「電子メールアドレスから」をカスタマイズすると、ブランドと一貫性を持たせることができます。お客様に **ドメイン名****の**置き換えをLivefyreがお勧めします。（デフォルトは **noreply@livefyre.com**です）。ご使用のネットワーク用のLivefyreデータベースの設定については、お好みの「電子メールアドレスから」をお使いのテクニカルインテグレーションマネージャーに渡してください。

   >[!NOTE]
   >
   >ネットワークに対する電子メール通知を無効にするには、このフィールドを空白のままにしておきます

* **[!UICONTROL Email Logo]**

   電子メール通知に表示されるロゴは、Studioの **ネットワーク設定** ページの「ブランディング」タブを使用して、デフォルトのLivefyreロゴではなく、会社のロゴを表示するようにカスタマイズできます。このカスタマイズは、サイトレベルではなくネットワークレベルでのみ利用でき、有料Livefyreのお客様のみ利用できます。

* **[!UICONTROL Custom Templates]**

   必要に応じて、完全にカスタマイズされた電子メールテンプレートを実装できます。ただし、これにはいくつかの開発作業が必要で、プロフェッショナルサービスの費用がかかる可能性があります。詳しくは、担当のアカウントマネージャーにお問い合わせください。



この機能を使用するアプリ:

* [カルーセル](/help/using/c-about-apps/c-carousel-app/c-carousel-app.md#c_carousel_app)
* [コメント](/help/using/c-about-apps/c-comments/c-comments.md)
* [Feature Card](/help/using/c-about-apps/c-feature-card-app/c-feature-card-app.md#c_feature_card_app)
* [メディアウォール](/help/using/c-about-apps/c-media-wall-app/c-media-wall-app.md#c_media_wall_app)
* [レビュー](/help/using/c-about-apps/c-reviews-app/c-reviews-app.md#c_reviews_app)
