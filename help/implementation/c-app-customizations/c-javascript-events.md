---
description: 会話アプリ（Comments、Chat、Live Blog、Reviews、Sidenotes など）用に JavaScript をバインドできるものに対して使用できるイベントです。
title: JavaScriptイベントの定義と例
exl-id: 5b865974-69aa-4d51-ac26-60f1d8a114fc
translation-type: tm+mt
source-git-commit: a2449482e617939cfda7e367da34875bf187c4c9
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 11%

---

# JavaScriptイベントの定義と例{#javascript-events-definitions-and-examples}

会話アプリ（Comments、Chat、Live Blog、Reviews、Sidenotes など）用に JavaScript をバインドできるものに対して使用できるイベントです。

Livefyreは、Livefyre Appsでユーザーのアクティビティを追跡するJavaScriptイベントを提供しています。 例えば、ユーザーがTwitterやFacebookにコンテンツを「いいね！」したり共有したりした場合、または新しいコンテンツが投稿された場合に、ページを更新したい場合があります。

また、Livefyreでは、サードパーティの解析イベント(Adobe AnalyticsJS、Google Analytics、Dynamic Tag Managementなど)に統合を追加して、アプリのイベントを追跡することもできます。 詳しくは、サードパーティのIntegration Managerを使用して正しいイベントを提供してください。

これらのイベントに連結するには、ページ上でアプリをインスタンス化する際に、次のコードをページに追加します。 イベント名を`{eventName}`に置き換えます。

```
Livefyre.require(['fyre.conv#3'], function(Conv) { 
   new Conv(networkConfig, [convConfig], function(widget) { 
      widget.on('{eventName}', function (data) { 
         // Do something, perhaps using data 
      }); 
   }); 
});
```

>[!NOTE]
>
>データオブジェクトは、すべてのイベントハンドラーに対して提供されます。 データオブジェクトの例は、各イベントの後に続きます。

## commentPosted {#section_qfr_51p_xz}

あるユーザーがコメントを投稿しました。

* 親がnullの場合は新しいコメントです。
* 親が「なし」の場合は、編集済みのコメントです。
* 親の数値は、返信の親IDです。

```
data = { 
   authorId: "_u2012@livefyre.com" // The ID of the author of the comment  
   parent: "893549"  
      // The ID of the comment that this new comment is in reply to, else null 
   bodyHtml: "<p>42</>" // The HTML of the submitted Content 
   sharedToFacebook:true // Whether the comment was also posted to Facebook 
   sharedToTwitter:false // Whether the comment was also posted to Twitter 
   title: "demo title" // The title of the review (exists only for Reviews) 
   rating: [90] // Array of ratings for the review (exists only for Reviews) 
} 
```

## commentFlagged {#section_szy_s1p_xz}

ユーザーがコメントにフラグを付けました。

```
data = { 
   targetId: "789347" // The ID of the comment that was flagged 
   type: ["disagree"] // The type of flag 
   notes: ["I don't entirely agree with this post"] // A note/reason for the flag 
}
```

## commentLinked {#section_vc1_r1p_xz}

ユーザーがコメントに「いいね！」をしました。

```
data = { 
   targetId: "245625" // The ID of the comment that was liked 
   targetAuthorId: "i_am_author@livefyre.com"  
      // The ID of the author of the comment that was liked 
} 
```

## commentShared {#section_nqb_31p_xz}

あるユーザーがストリームからコメントを共有しました。 (このイベントは、ユーザーがコメントエディターから共有した場合には実行されません)。 このイベントは、「共有」ボタンがクリックされた場合にトリガーされます。

```
data = { 
   targetId: "256255" // The ID of the comment that was shared 
   sharedToFacebook:false // Whether the comment was shared to Facebook 
   sharedToTwitter:true // Whether the comment was shared to Twitter 
}
```

## commentCountUpdated {#section_qdq_f1p_xz}

この会話で表示されているコメントの総数が変更されました（増分または減分）。

```
data: 34 // The total number of visible comments in the conversation (integer). 
```

## userLoggedIn {#section_yjt_vz4_xz}

ユーザーがログインしました。

```
data = { 
   avatar: "https://gravatar.com/avatar/50.jpg"  
      // Link to logged in user's avatar image 
   displayName: "NewUser" // Display name of the logged in user 
   id: "newuser@livefyre.com" // ID of the logged in user 
   isModerator:false // Boolean indicating whether logged in user is a moderator 
}
```

## userLoggedOut {#section_tsg_5z4_xz}

ユーザーがログアウトしました。

データが未定義です。

## socialMention {#section_a1w_tz4_xz}

ユーザーがコメントに@メンションを含めました。 次の配列を返します。

```
data = { 
   id: '111111@fb.gw.livefyre.com' // ID of the mentioned user 
   displayName: 'testUser' // Display name of mentioned user 
   message: "@testUser Wow, I can't believe it either!"  
      // Message that was sent to the particular user 
   provider: 'twitter' // Provider to which the mention was shared 
} 
```

## commentFeatured

モデレーターユーザーがコメントを表示しました。 次の配列を返します。

```
data = { 
   targetId: "134234" // The ID of the comment that was featured 
   targetAuthorId: "i_am_author@livefyre.com"  
      // The ID of the author of the comment that was featured 
}
```

## initialRenderComplete {#section_odc_4z4_xz}

コメントストリームが読み込まれ、コンテンツの初期セットがサーバーから取得され、ユーザーに表示されました。

データが未定義です。

## showMore {#section_pqg_nz4_xz}

ユーザーが&#x200B;**[!UICONTROL Show More]**&#x200B;ボタンをクリックしました。

データが未定義です。

## userFollowed {#section_xxw_jz4_xz}

ユーザーが&#x200B;**[!UICONTROL Follow]**&#x200B;ボタンをクリックするとtrueを返し、ストリームにコンテンツが投稿されるとfalseを返します。

```
data = { 
   id: 'authorId@livefyre.com', 
   optIn: true 
}
```

## userUnfollowed {#section_wm1_gz4_xz}

ユーザーが「**フォロー解除**」ボタンをクリックするとtrueを返し、ストリームにコンテンツが投稿されるとfalseを返します。

```
data = { 
   id: 'authorId@livefyre.com', 
   optOut: true 
}
```
