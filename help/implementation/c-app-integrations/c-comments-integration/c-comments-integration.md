---
description: ページ上のライブコメントを有効にします。
seo-description: ページ上のライブコメントを有効にします。
seo-title: コメント
solution: Experience Manager
title: コメント
uuid: decad9b0-2074-4748- bd77-914008817bfa
translation-type: tm+mt
source-git-commit: 566ea2587f101202045488e9f4edf73ece100293

---


# コメント{#comments}

ページ上のライブコメントを有効にします。コメントを使用すると、デフォルトのコメントシステムをページ上のリアルタイムの会話に置き換えることができます。

## 統合{#concept_4093E8BAA96A464BA74D263DA031C0B0}

コメントアプリの埋め込みは、はじめに/アプリの埋め込みで説明されているコアアプリを埋め込むためのプロセスに従います。

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

CollectionMetaセクションの作成に記載されているとおり、CollectionMetaはエンコードされたJSONオブジェクトです。上記の例では、JSONオブジェクトはJWTエンコード前に次の形式を使用します。

```
{ 
"url": "articleUrl",  
"articleId": "articleId",  
"type": "livecomments",  
"title": "articleTitle" 
}
```

## NetworkConfigオブジェクト {#c-networkconfig-object}

`NetworkConfig` オブジェクトは、ネットワークユーザーの認証システムをカスタマイズするJSONオブジェクトです。
`NetworkConfig` オブジェクトは、次のパラメーターを含むJSONオブジェクトです。

| パラメータ | タイプ | 説明 |
|---|---|---|
| **AuthDelegate** | *必須* オブジェクト | カスタムネットワークユーザーの認証システムをカスタマイズするために使用します。 |
| **ネットワーク** | 文字列 *が必要です* | Livefyreによって提供されるネットワーク名。次に例を示します。 *yourname. fyre. co.* |
| **AttachmentDelegate** | *オプション* オブジェクト | アプリケーションストリームに表示されるメディア添付のタイプを指定するために使用します。詳しくは、メディアの制限を [](/help/implementation/c-app-customizations/c-restrict-media.md#c_restrict_media)参照してください。 |
| **文字列** | *オプション* オブジェクト | Livefyre CoreアプリケーションのいずれかのHTML要素のテキスト文字列をカスタマイズするために使用します。詳しくは [、「文字列のカスタマイズ](/help/using/c-settings-other/c-translation-sets/c-localize-strings.md)」を参照してください。 |

## contentConfigオブジェクト {#c-convconfig-object}

`convConfig` オブジェクトは、Livefyreアプリケーションがページ上でレンダリングするコンテンツを指定するために使用するJSONオブジェクトです。

>[!NOTE]
>
>ここに示す `convConfig` オブジェクトパラメーターは、レビューアプリには適用されません。`convConfig` オブジェクトを使用したレビューアプリに関する統合情報については、「レビュー統合」を参照してください。

`ConvConfig` このオブジェクトには、次の必須パラメータが含まれています。

| パラメータ | タイプ | 説明 |
|--- |--- |--- |
| **articleId** | *必須* 文字列 | サイト内でコレクションを一意に識別します。通常、これはCMS内のデータベースのプライマリキーまたはポストIDに対応します。次に例を示します。"post-42"。255文字の制限。注意:記事のURLをarticleIDとして使用する場合は、文字列がMD5またはSHA-1でエンコードされていることを確認してください。 |
| **authPageLoadAd** | *オプション* のブール値 | コメントアプリに適用:ユーザーのコメントを認証プロセス中にローカルに保存するかどうかを制御できます。trueの場合、ユーザーがコメントを入力してからアプリにログインすると、コメントはローカルに保存され、ログインとページの更新後にコンテンツフィールドに再入力されます。falseの場合、ログインプロセス中に入力したコンテンツが消去され、再入力する必要があります。 |
| **CollectionMeta** | *必須* 文字列 | コレクションに関するJWTエンコードメタデータ。詳しくは [、CollectionMeta](#c_collectionmeta_object) Objectを参照してください。 |
| **el** | *必須* 文字列 | コンテンツストリームがレンダリングするDOM要素のIDです。 |
| **siteID** | *必須* 文字列 | コレクションが属するWebサイトまたはアプリケーションのLivefyre- provided ID。次に例を示します。"303617". |

>[!NOTE]
>
>この `app` パラメーターは、Comments App実装では必須ではありません。

`ConvConfig` このオブジェクトには、次のオプションのパラメーターを含めることもできます。

| パラメータ | タイプ | 説明 |
|--- |--- |--- |
| **actionButtons** | *オプション* の配列 | 共有ボタンとフラグボタンの横にあるコンテンツの一部に追加するカスタムアクションボタンの配列。詳しくは、「カスタムボタンの追加」を参照してください。 |
| **アニメーション** | *オプション* のブール値 | Livefyreアプリ内でアニメーションを実行するかどうかを定義します。アニメーションを無効にするにはfalseに設定します。デフォルトはtrueです。 |
| **匿名フラグgingEnabled** | *オプション* のブール値 | ゲストユーザーにコンテンツフラグを設定するかどうかを定義します。初期設定はtrueです。 |
| **browserType** | *オプション* の文字列 | 表示する表示コンテンツのデバイスを定義します。これにより、入力デバイスの種類に合わせてCSSが変更され、一部の機能が変更されます。デスクトップ、モバイル、タブレットのオプションがあります。（空白の場合、表示形式のGoogleエージェントの決定はデフォルトで行われます）。 |
| **checksum** | *推奨* 文字列 | CollectionMetaの現在の状態を識別します。この値を変更すると、LiveFyreは、CollectionMetaの新しい値を使用してサーバー上のデータを更新します。 |
| **dateTimeFormat** | *オプション* の文字列オブジェクト関数 | ストリーミングコンテンツのdatetime形式を指定します。詳しくは、日付およびタイムスタンプのカスタマイズを参照してください。 |
| **disableVariables** | *オプション* のブール値 | アバターがアプリケーションストリーム内でレンダリングされるのを防ぎ、ブラウザーに読み込まれた項目数を削減します。初期設定はfalseです。 |
| **disableIE8Shim** | *オプション* のブール値 | HTML5要素がサポートされるように、LivefyreがInternet Explorer8に対して使用するデフォルトのシエフを無効にします。Livefyreは次のプロジェクトを使用します。 [https://github.com/aFarkas/html5shiv](https://github.com/aFarkas/html5shiv) .初期設定はfalseです。注意:この値がfalseの場合、Internet Explorer8のサポートに対してLivefyre Chatを呼び出す前に、一部の並べ替えのPolyfillを使用する必要があります。 |
| **disableThirdPartyAnalytics** | *オプション* のブール値 | Livefyreが内部測定に使用するサードパーティの分析システム（QuantingおよびGoogle Analytics）を無効にします。初期設定はfalseです。 |
| **editorCSS** | *オプション* オブジェクト | コメントエディターのスタイル設定をカスタマイズするために使用します。エディターフィールドの背景色と、エディター内に表示されるフォントの色、サイズおよびファミリーのスタイルを設定できます。次に例を示します。 `{background: ‘#ccc’, color: ‘red’, font: ’30px “Helvetica Neue”, Helvetica, Arial, Geneva, sans-serif’}` |
| **initialNumVisible** | *optional* integer | 読み込み時に、アプリに表示されるコメントのデフォルト数を設定できます。1~50の整数を指定できます。 |
| **initialNumVisibleManagement** | *optional* integer | 読み込み時に、アプリに表示されるレガシーコンテンツ項目のデフォルト数を設定できます。1~50の整数を指定できます。このパラメーターを指定しない場合、初期設定はinitialNumVisibleです。次に例を示します。コレクションにアクティブな100個のアクティブなコメントと100個のレガシーコメントが含まれている場合は、initalNumVisibleを設定します。10およびinitialNumVisibleLegacy:5.アクティブなコメントを10件表示（「表示を増やす」ボタン付き）+5アーカイブコメント（「さらに表示」ボタン付き） |
| **maxVisible** | *optional* integer | チャットアプリの最上位レベルのコンテンツの最大表示数を設定します。新しいコンテンツストリームの場合、ストリームの下部にあるコンテンツがページから削除されます。"Show more…」ボタンをクリックすると、パラメーターは無視され、ユーザーは必要なだけコンテンツを表示できます。（このパラメーターを使用して、ページに表示される項目の数を高速ストリームで制御します）。 |
| **postToButtons** | *オプション* の配列 | ライブブログアプリを埋め込むときに表示するプロバイダーを設定するために使用します。使用可能なオプションは、tw（Twitter）、fb（Facebook）およびli（LinkedIn）です。デフォルトは [ tw， fb ]です。 |
| **readOnly** | *オプション* のブール値 | コレクションのすべてのインタラクティブ機能を無効にします。trueの場合、ユーザーはストリームにログインできず、投稿、編集、編集、または「いいね!"のコンテンツができません。trueの場合、ユーザーはコンテンツをフラグ付けおよび共有できます。初期設定はfalseです。 |
| **stream** | *オプション* オブジェクト | アプリのストリーミングを設定するためのオプションが含まれます。 |
| **stream. chatchup** | *optional* integer | ストリームが読み込む時間の前の秒数を指定します。デフォルトでは、Livefyreは50個のコンテンツを読み込み、それらと現在の時刻に送信されたすべてのコンテンツを読み込みます。非常に高速な使用例では、コンテンツを迅速に投稿して、アプリが現在のアプリを検出できるようにすることができます。この設定を使用して、コンテンツが投稿されるまでの秒数（最初のコンテンツの読み込み後）を定義します。 |
| **stream. delay** | *optional* integer | ストリーミングリクエストの間隔を秒数で指定します。このパラメーターは、コンテンツのフローを制御し、DOMが更新される頻度を制御するために使用します。注意:設定が大きすぎる場合、ストリームはフォールバックできます。 |


>[!NOTE]
>
>アプリの初期化時に1つ以上 `convConfig` のオブジェクトを渡すことで、同じページに複数のアプリを表示できます。追加のアプリではブラウザーリソースが使用され、数が増えるとパフォーマンスが低下することがあります。

## CollectionMetaオブジェクト {#c-collectionmeta-object}

`CollectionMeta` オブジェクトは、コレクション内に格納するメタデータを指定するJSONオブジェクトです。

`CollectionMeta` は、セキュリティのためにLivefyreに渡す前に常にエンコードされます。エンコードされた値が上記の `ConvConfig` オブジェクトに渡されます。

>[!NOTE]
>
>`CollectionMeta` JSONオブジェクトをエンコードするには、サーバーサイドコードを追加する必要があります。詳しくは、サーバー側トークンの構築を参照してください。

| パラメータ | タイプ | 説明 |
|--- |--- |--- |
| **articleId** | *必須* 文字列 | コレクションの一意のID。 |
| **title** | *必須* 文字列 | コレクションに適用するタイトル。これは、アプリを表示するページのタイトルに対応することがよくあります。次に例を示します。「統合は非常に楽しい!"<br>**注意:** タイトルの最大文字長は255文字です。タイトルフィールドはHTMLエンティティをサポートしていません。UTF-8を使用して特殊文字をエンコードしてください。 |
| **url** | *必須* 文字列 | このコレクションに付加する正規の絶対URLです。このURLは、FacebookおよびTwitter、電子メール通知およびLivefyre Studioで共有されたコンテンツからアプリに戻るリンクを生成するために使用されます。<br>**注意** Livefyreでは完全修飾ドメイン名を使用する必要があります。ローカルセットアップを解決するポート番号またはコールバックは不要です。ローカルでテストする場合は、有効なベースURLドメインを使用することをお勧めします。<br>次に例を示します。 `https://customer.com` は有効ですが、有効 `https://localhost:5995` ではありません。完全修飾ドメイン名を受け入れるようにローカルWebサーバーをセットアップしたら、コールバックまたは解決は不要です。ローカル開発は、期待どおりに続行できます。 |
| **type** | *必須* 文字列 | コレクションタイプ。`livechat`必要です。 |

`CollectionMeta` このオブジェクトには、次のオプションのパラメーターを含めることもできます。

| パラメータ | タイプ | 説明 |
|---|---|---|
| **タグ** | *オプション* の文字列 | 単一のキーワードまたはフレーズのコンマ区切りリスト。Studio内のタグまたは検索APIでコレクションを検索します。 <br> **注意:** Studioで追加したタグにスペースを含めることができますが、API経由で入力されたタグは使用できません。アンダースコアを使用して、UIにスペースを表示するタグを定義します。（例:を使用 `Monday_Quarterback` して、Studioに月曜のQuarterbackを表示します。） |

## イベントハンドラーの追加 {#concept_06D8B811C98B4CC6B38C6340EBA176E5}

イベントハンドラーを登録するには、アプリケーションのコールバック関数内でwidget. on呼び出しを使用します。

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