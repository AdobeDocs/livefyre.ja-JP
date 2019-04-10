---
description: 単一ページで複数のコレクションを表示します。
seo-description: 単一ページで複数のコレクションを表示します。
seo-title: 複数のコレクション
solution: Experience Manager
title: 複数のコレクション
uuid: 9675ffd7-1a59-42a1- b3ba-40af1744felet1
translation-type: tm+mt
source-git-commit: 566ea2587f101202045488e9f4edf73ece100293

---


# 複数のコレクション {#multiple-collections}

単一ページで複数のコレクションを表示します。

サイト上の単一のページに複数のコレクションを含めることができます。例えば、イベントを公開するには、イベント中にライブブログまたはチャットのディスカッションを行って、そのイベント中に別のアプリを、ソーシャルWebの周囲から関連付けられたコンテンツを表示します。または、チャットをサイドと共に記事の下にコメントアプリを含めることもできます。

ページ上で複数の会話を取得するには、1つまたは複数の設定を配列に追加し、その配列をロード呼び出しに渡します。例えば、

```
<html> 
<head> 
<script src='//cdn.livefyre.com/Livefyre.js'></script> 
</head> 
<body> 
<script type="text/javascript"> 
convConfig1 = {"collectionMeta": <COLLECTION META 1>, 
             "checksum": <CHECKSUM 1>, 
             "siteId": <SITE ID>, 
             "articleId":"1", 
             "el":"livefyre"}; 
convConfig2 = {"collectionMeta": <COLLECTION META 2>, 
             "checksum": <CHECKSUM 2>, 
             "siteId": <SITE ID>, 
             "articleId":"2", 
             "el":"livefyre"}; 
convConfig3 = {"collectionMeta": <COLLECTION META 3>, 
             "checksum": <CHECKSUM 3>, 
             "siteId": <SITE ID>, 
             "articleId":"3", 
             "el":"livefyre"}; 
  
Livefyre.require(['fyre.conv#prod'],function(Conv) { 
    new Conv({"network": "<NETWORK NAME>"}, 
    [convConfig1], 
    function(app) {  
        window.changeConv = app.changeCollection; 
    } 
    ); 
}); 
</script> 
  
<div id="livefyre"></div> 
<button onclick="window.changeConv(convConfig1);">Conv 1</button> 
<button onclick="window.changeConv(convConfig2);">Conv 2</button> 
<button onclick="window.changeConv(convConfig3);">Conv 3</button> 
</body> 
</html>
```