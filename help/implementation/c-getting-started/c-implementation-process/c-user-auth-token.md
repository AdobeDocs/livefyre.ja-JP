---
description: この節では、ユーザーのアプリへのログインに必要なユーザー認証トークンを作成するUserAuth JSONオブジェクトを生成する方法について説明します。
title: ユーザー認証トークン
exl-id: 564144dd-6db4-447b-80ac-b743ecac833d
translation-type: tm+mt
source-git-commit: a2449482e617939cfda7e367da34875bf187c4c9
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 2%

---

# ユーザー認証トークン{#user-auth-token}

この節では、ユーザーのアプリへのログインに必要なユーザー認証トークンを作成するUserAuth JSONオブジェクトを生成する方法について説明します。

この節では、ユーザーのアプリへのログインに必要なユーザー認証トークンを作成するUserAuth JSONオブジェクトを生成する方法について説明します。

トークンを作成するには、希望の言語ライブラリを使用して次のパラメーターを渡します。

| パラメーター | タイプ | 説明 |
|---|---|---|
| networkName | 文字列&#x200B;*必須* | Livefyreネットワークの名前（Livefyreが提供します）。 |
| networkKey | 文字列&#x200B;*必須* | この特定のネットワークの秘密キー（Livefyreが提供）。 |
| userId | 文字列&#x200B;*必須* | ユーザー管理システムに保存されている、ログインするユーザーのID（英数字、ダッシュ、アンダースコアおよびドット文字のみ使用できます）。[a-zA-Z0-9_-.] を参照してください）。**注意：userId** は一意である必要があります。 |
| expires | 整数&#x200B;*必須* | トークンの有効期限が切れる時間（秒）。 **注意：** この値は、floatとして渡すこともできます。生成されたJSON Webトークンは、UNIXエポック時間にこの値を格納します。 |
| displayName | 文字列&#x200B;*必須* | UIおよびコメントでこのユーザーを識別するテキスト。 (最大文字数：50.) |

## Java {#section_b42_mjz_1cb}

```
network.buildUserAuthToken(userId, displayName, expires); 
 
```

## NodeJS {#section_c42_mjz_1cb}

```
network.buildUserAuthToken(userId, displayName, expires); 
```

## PHP {#section_d42_mjz_1cb}

```
$network->buildUserAuthToken(userId, displayName, expires); 
```

## Python {#section_e42_mjz_1cb}

```
network.build_user_auth_token(userId, displayName, expires) 
```

## Ruby {#section_f42_mjz_1cb}

```
network.build_user_auth_token(userId, displayName, expires) 
```

>[!NOTE]
>
>ネットワークキーがLivefyreデモサイトのアカウントで共有されません。 Livefyreが環境のプロビジョニングを完了すると、ネットワークキーを受け取ります。 このキーは秘密にする必要があります。
