---
title: スマートタグ
description: スマートタグ
exl-id: cbbc5550-d6cf-42e5-bce7-2c270cc968cd
translation-type: tm+mt
source-git-commit: a2449482e617939cfda7e367da34875bf187c4c9
workflow-type: tm+mt
source-wordcount: '273'
ht-degree: 0%

---

# スマートタグ{#smart-tags}

Livefyreは、Adobe Senseiのコンピューター・ビジョン技術を使用して、ライブラリに保存またはアップロードした画像やビデオに自動的にタグ付けします。

スマートタグを使用すると、コンテンツの管理、検索およびキュレーションにかなりの時間を節約できます。 スマートタグを使用すると、次のことができます。

* テキストだけでなく、画像とビデオのコンテンツに基づいて、保存およびアップロードした画像とビデオを検索し、正確なコンテンツを得る
* テキストだけでなく、画像やビデオを分析する正確な検索用語に基づいて、ストリーム内のコンテンツを収集する

画像またはビデオを保存またはアップロードすると、Adobe Senseiは自動的にコンテンツをレビューし、3つのカテゴリに135,000の分類子を使用してタグ付けします。

* 特徴（例えば、猫、犬、ピラミッド、ランドマーク）
* カテゴリ（例：旅行、観光、美容など）
* 美的特性（画質、第3のルールなど）
* SFW/NSFW(これにより、NSFWイメージを自動的にフィルタし、ストリームとUGCライブラリの安全性を向上

スマートタグランキングアルゴリズムは、スマートタグの信頼性スコアを使用してコンテンツをフィルターし、コンテンツの新規コンテンツの数と、ユーザーがコンテンツに与えた星の数を示します。

**ビデオのスマートタグ**

機能の詳細：

* スマートタグは、MP4、.aviおよび.movビデオ形式に適用されます
* サポートされるビデオの最大時間は60秒または50MBです
* スマートタグは、ソーシャル検索、ストリームおよびライブラリ内のアップロードされたビデオファイルで使用できます

タグの種類：

* 機能タグ：画像の機能タグ（例えば、猫、犬、ピラミッド、ランドマーク）と同じです。
* アクションタグ：1つのフレームだけでなく、複数のフレームで発生する機能を特定する。 これらは、ビデオのコンテンツを要約するのにより効果的です。

スマートタグに関する追加情報については、[Stream Rule Options for All Stream Rules](../../c-streams/c-stream-rule-options-for-all-stream-rules.md#c_stream_rule_options_for_all_stream_rules)を参照してください。
