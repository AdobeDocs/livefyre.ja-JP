---
description: ページでライブコメントを有効にする。
title: コメント
exl-id: d62b3dc1-3c5e-45f6-9b21-ea1edcda9812
translation-type: tm+mt
source-git-commit: a2449482e617939cfda7e367da34875bf187c4c9
workflow-type: tm+mt
source-wordcount: '1468'
ht-degree: 3%

---

# コメント{#comments}

ページでライブコメントを有効にする。 コメントを使用すると、デフォルトのコメントシステムをページ上のリアルタイム会話に置き換えることができます。

## 統合 {#concept_4093E8BAA96A464BA74D263DA031C0B0}

コメントアプリの埋め込みは、はじめに/アプリの埋め込みで説明されているコアアプリの埋め込みの手順に従って行います。

### 例

```
<html> 
  <head> 
    <script src="//cdn.livefyre.com/Livefyre.js"> 
    </script> 
  </head> 
<body> 
    <script type="text/javascript"> 
    var networkConfig = { 
      network: 'domainName' 
    }; 
    var convConfig = { 
      siteId: 'siteId', 
      articleId: 'articleId', 
      el: 'livefyre', 
      collectionMeta: 'collectionMeta', 
      checksum: 'checksum' 
    }; 
    
    Livefyre.require(['fyre.conv#3', 'auth'], function(Conv, auth) { 
        new Conv(networkConfig, [convConfig], function(commentsWidget) {}); 
        auth.delegate({ 
            login: function (callback) { 
                callback(null,{livefyre:'<userauthtoken>'}); 
            }, 
        }); 
    }); 
  
    </script> 
    <div id="livefyre"> 
    </div> 
   </body> 
</html>
```

「CollectionMetaの構築」の節で説明したように、CollectionMetaはエンコードされたJSONオブジェクトです。 上記の例では、JSONオブジェクトはJWTエンコードされる前に次の形式を取ります。

```
{ 
"url": "articleUrl",  
"articleId": "articleId",  
"type": "livecomments",  
"title": "articleTitle" 
}
```

## NetworkConfigオブジェクト{#c-networkconfig-object}

`NetworkConfig`オブジェクトは、ネットワークユーザーの認証システムをカスタマイズするJSONオブジェクトです。
`NetworkConfig`オブジェクトは、次のパラメーターを含むJSONオブジェクトです。

| パラメーター | タイプ | 説明 |
|---|---|---|
| **authDelegate** | **  requiredobject | カスタムネットワークユーザーの認証システムをカスタマイズするために使用します。 |
| **network** | 文字列&#x200B;*必須* | Livefyreが提供するネットワーク名。 次に例を示します。*yourname.fyre.co.* |
| **attachmentDelegate** | ** optionalobject | アプリストリームに表示されるメディア添付ファイルの種類を指定するために使用します。 詳しくは、[メディアの制限](/help/implementation/c-app-customizations/c-restrict-media.md#c_restrict_media)を参照してください。 |
| **文字列** | ** optionalobject | 任意のLivefyreコアアプリ内のHTML要素のテキスト文字列をカスタマイズするために使用します。 詳しくは、「[文字列のカスタマイズ](/help/using/c-settings-other/c-translation-sets/c-localize-strings.md)」を参照してください。 |

## ConvConfigオブジェクト{#c-convconfig-object}

`convConfig`オブジェクトは、Livefyre Appがページ上でレンダリングするコンテンツを指定するために使用するJSONオブジェクトです。

>[!NOTE]
>
>ここに示す`convConfig`オブジェクトパラメーターは、Reviewsアプリには適用されません。 `convConfig`オブジェクトを使用するReviewsアプリに関する統合情報については、「統合のレビュー」を参照してください。

`ConvConfig`オブジェクトには、次の必須パラメーターが含まれています。

| パラメーター | タイプ | 説明 |
|--- |--- |--- |
| **articleId** | ** 必須文字列 | サイト内のコレクションを一意に識別します。 通常、これはCMS内のデータベースの主キーまたは投稿IDに対応します。 次に例を示します。&quot;42より後&quot; 上限 255 文字.  注意： 記事URLをarticleIdとして使用する場合、文字列がMD5またはSHA-1でエンコードされていることを確認します。 |
| **authPageReload** | **  optionalboolean | コメントアプリに適用：認証プロセス中にユーザーのコメントをローカルに保存するかどうかを制御できます。 trueの場合、ユーザーがコメントを入力してからアプリにログインすると、コメントはローカルに保存され、ログインおよびページ更新後にコンテンツフィールドに再入力されます。 falseの場合、入力した内容はログイン処理中に消去され、再入力する必要があります。 |
| **collectionMeta** | ** 必須文字列 | コレクションに関するJWTエンコードされたメタデータ。 詳しくは、[CollectionMeta](#c_collectionmeta_object)オブジェクトを参照してください。 |
| **el** | ** 必須文字列 | コンテンツストリームがレンダリングされるDOM要素のID。 |
| **siteId** | ** 必須文字列 | コレクションが属するWebサイトまたはアプリケーションのLivefyre提供ID。 次に例を示します。&quot;303617&quot; |

>[!NOTE]
>
>`app`パラメーターは、コメントアプリの実装には必要ありません。

`ConvConfig`オブジェクトには、次のオプションのパラメーターを含めることもできます。

| パラメーター | タイプ | 説明 |
|--- |--- |--- |
| **actionButtons** | ** optionalarray | 共有ボタンとフラグボタンの横のコンテンツに追加するカスタムアクションボタンの配列です。 詳しくは、「カスタムボタンの追加」を参照してください。 |
| **アニメーション** | ** optionalboolean | アニメーションをLivefyreアプリ内で実行するかどうかを定義します。 アニメーションを無効にするには、falseに設定します。 デフォルトはtrueです。 |
| **anonymousFlaggingEnabled** | ** optionalboolean | ゲストユーザーにコンテンツにフラグを付けるオプションを持たせるかどうかを定義します。 初期設定は true です。 |
| **browserType** | ** optionalstring | 表示コンテンツを生成するデバイスを定義します。 これにより、CSSと一部の機能が、入力デバイスタイプに合わせて変更されます。 デスクトップ、モバイル、タブレットのオプションがあります。 （空白の場合、表示形式に対するGoogleエージェントの決定がデフォルトになります）。 |
| **checksum** | ** 推奨文字列 | CollectionMetaの現在の状態を示します。 この値を変更すると、Livefyreによってサーバー上のデータがCollectionMetaの新しい値で更新されます。 |
| **datetimeFormat** | **  optionalstringオブジェクト関数 | ストリームコンテンツの日時形式を指定します。 詳しくは、日付とタイムスタンプのカスタマイズを参照してください。 |
| **disableAvatars** | ** optionalboolean | アバターがアプリストリーム内にレンダリングされないようにし、ブラウザーに読み込まれるアイテムの数を減らします。 デフォルトは false です。 |
| **disableIE8Shim** | ** optionalboolean | LivefyreがInternet Explorer 8に多重入力するように使用する初期設定のshivを無効にして、HTML5要素がサポートされるようにします。 Livefyreは次のプロジェクトを使用します。 [https://github.com/aFarkas/html5shiv](https://github.com/aFarkas/html5shiv). デフォルトは false です。注意： この値がfalseの場合、Internet Explorer 8のサポートのためにLivefyre Chatを呼び出す前に、何らかのポリフィルを使用する必要があります。 |
| **disableThirdPartyAnalytics** | ** optionalboolean | Livefyreが内部測定に使用する可能性があるサードパーティの解析システム(QuantserveおよびGoogle Analytics)を無効にします。 デフォルトは false です。 |
| **editorCss** | ** optionalobject | コメントエディターのスタイル設定をカスタマイズするために使用します。 エディターフィールドの背景色と、エディター内に表示されるテキストのフォントの色、サイズ、ファミリーのスタイルを設定できます。  例えば、`{background: ‘#ccc’, color: ‘red’, font: ’30px “Helvetica Neue”, Helvetica, Arial, Geneva, sans-serif’}` |
| **initialNumVisible** | ** optionalinteger | 読み込み時にアプリに表示されるコメントのデフォルト数を設定できます。 1 ～ 50の整数を指定できます。 |
| **initialNumVisibleLegacy** | ** optionalinteger | 読み込み時にアプリに表示されるレガシーコンテンツ項目のデフォルト数を設定できます。 1 ～ 50の整数を指定できます。 このパラメーターを指定しない場合、デフォルトはinitialNumVisibleです。  次に例を示します。コレクションに100個のアクティブなコメントと100個のレガシーコメントが含まれる場合、10個のアクティブなコメント（「表示を増やす」ボタンを含む） + 5個のアーカイブコメントを表示するには、initalNumVisible:10およびinitialNumVisibleLegacy:5を設定します。 |
| **maxVisible** | ** optionalinteger | チャットアプリで表示される最上位レベルのコンテンツの最大部分の数を設定します。 で新しいコンテンツストリーム部分が発生した場合、ストリームの下部にあるコンテンツはページから削除されます。 「表示を増やす」ボタンをクリックすると、パラメーターは無視され、ユーザーは必要な分だけコンテンツを自由に表示できます。 （このパラメーターを使用して、高速ストリームでページに表示するアイテム数を制御します）。 |
| **postToButtons** | ** optionalarray | ライブブログアプリを埋め込む際に表示するプロバイダーを設定するために使用します。 選択可能なオプションは、2つ(Twitter)、fb(Facebook)、li(LinkedIn)です。 デフォルトは[ tw , fb ]です。 |
| **readOnly** | ** optionalboolean | コレクションのすべてのインタラクティブ機能を無効にします。 trueの場合、ユーザーはストリームにログインできず、投稿、編集、返信または「いいね！」のコンテンツを実行できません。 trueの場合、ユーザーはコンテンツにフラグを付けて共有できます。 デフォルトは false です。 |
| **流れ** | ** optionalobject | アプリのストリーミングを設定するオプションが含まれます。 |
| **stream.catchup** | ** optionalinteger | ストリームを読み込む現在の時点までの秒数を指定します。 デフォルトでは、Livefyreは50個のコンテンツを読み込み、その後、これらと現在の間に送信されたすべてのコンテンツを読み込みます。 非常に高速な使用例では、コンテンツの投稿が非常に早すぎて、アプリが現在に「追い付く」ことがあります。 この設定を使用して、（最初のコンテンツの読み込み後に）コンテンツが投稿されるまでの秒数を定義します。 |
| **stream.delay** | ** optionalinteger | ストリーミング要求間の秒数を指定します。 このパラメーターは、コンテンツのフローを制御したり、DOMの更新頻度を遅らせたりするのに役立ちます。  注意： 大きく設定すると、ストリームが遅れる可能性があります。 |


>[!NOTE]
>
>アプリの初期化中に1つ以上の`convConfig`オブジェクトを渡すと、同じページに複数のアプリを表示できます。 数が増えるにつれて、追加のアプリでブラウザーのリソースが使用され、パフォーマンスが低下する可能性があることに注意してください。

## CollectionMeta Object {#c-collectionmeta-object}

`CollectionMeta`オブジェクトは、コレクション内に格納するメタデータを指定するJSONオブジェクトです。

`CollectionMeta` は、セキュリティを確保するためにLivefyreに渡される前に常にエンコードされます。エンコードされた値は、上に示す`ConvConfig`オブジェクトに渡されます。

>[!NOTE]
>
>`CollectionMeta` JSONオブジェクトをエンコードするには、サーバー側のコードを追加する必要があります。 詳しくは、「サーバー側トークンの構築」を参照してください。

| パラメーター | タイプ | 説明 |
|--- |--- |--- |
| **articleId** | ** 必須文字列 | コレクションの一意のID。 |
| **title** | ** 必須文字列 | コレクションに適用するタイトル。 これは、多くの場合、アプリを表示するページのタイトルに対応します。  次に例を示します。「Integration is So Fun!」 <br>**注意：タイトル**  の最大文字長は255文字です。タイトルフィールドはHTMLエンティティをサポートしていません。 特殊文字はUTF-8を使用してエンコードしてください。 |
| **url** | ** 必須文字列 | このコレクションに添付する正規の絶対URLです。 このURLは、FacebookとTwitterで共有されたコンテンツ、電子メール通知およびLivefyre Studioからアプリへ戻るリンクを生成するために使用されます。  <br>**** 注意Livefyreでは、完全修飾ドメイン名を使用する必要があります。ローカルセットアップを解決するためのポート番号またはコールバックは必要ありません。ローカルでテストする場合は、有効なベースURLドメインを使用するようにしてください。 <br>次に例を示します。 `https://customer.com` は有効ですが、 `https://localhost:5995` は無効です。完全修飾ドメイン名を受け入れるようにローカルWebサーバーを設定した後は、コールバックや解決は必要なく、ローカル開発は期待どおりに続行できます。 |
| **type** | ** 必須文字列 | コレクションの種類です。 `livechat`にする必要があります。 |

`CollectionMeta`オブジェクトには、次のオプションのパラメーターを含めることもできます。

| パラメーター | タイプ | 説明 |
|---|---|---|
| **タグ** | ** optionalstring | 1つのキーワードまたはフレーズをコンマで区切ったリスト。 Studio内のタグまたは検索APIでコレクションを検索します。<br> **注意：Studioを通して追加されるタグにはスペースが含まれている** 場合がありますが、APIを通じて入力されるタグは含まれません。アンダースコアを使用して、UIにスペースを表示するタグを定義します。 (例：`Monday_Quarterback`を使ってStudioでMonday Quarterbackを表示します)。 |

## イベントハンドラーの追加{#concept_06D8B811C98B4CC6B38C6340EBA176E5}

イベントハンドラーを登録するには、アプリのコールバック関数内でwidget.on呼び出しを使用します。

### 例えば、

```
Livefyre.require(['fyre.conv#3'], function(Conv) { 
   new Conv(networkConfig, [convConfig], function(widget) { 
      widget.on('<strong><eventName></strong>', function (data) { 
         // Do something, perhaps using data 
      }); 
   }); 
});
```
