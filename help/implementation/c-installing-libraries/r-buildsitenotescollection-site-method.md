---
description: Sideisingタイプとしてインスタンス化されたCollectionオブジェクトを返します。ビルドプロセスを完了するには、Collectionオブジェクトからcreate_
  or_ update（）を実行します。
seo-description: Sideisingタイプとしてインスタンス化されたCollectionオブジェクトを返します。ビルドプロセスを完了するには、Collectionオブジェクトからcreate_
  or_ update（）を実行します。
seo-title: BuildSiteNotesCollectionサイトのメソッド
solution: Experience Manager
title: BuildSiteNotesCollectionサイトのメソッド
uuid: 2bfbc032-4c0c-48d2-8ce6-02460b38bd6c
translation-type: tm+mt
source-git-commit: 566ea2587f101202045488e9f4edf73ece100293

---


# BuildSiteNotesCollectionサイトのメソッド{#buildsitenotescollection-site-method}

Sideisingタイプとしてインスタンス化されたCollectionオブジェクトを返します。ビルドプロセスを完了するには、Collectionオブジェクトからcreate_ or_ update（）を実行します。

| 変数 | タイプ | 説明 |
|--- |--- |--- |
| title | 文字列 | コレクションのタイトル。 |
| articleId | 文字列 | サイト内のコレクションを識別するために選択した一意の記事ID。 |
| url | 文字列 | このコレクションの正規の絶対URLです。 |

## Javaの例 {#section_nyl_ycs_rz}

```
Collection collection = site.buildSidenotesCollection(title, articleId, url); 
```

## NodeJSの例 {#section_xkd_gds_rz}

```
var collection = site.buildSidenotesCollection(title, articleId, url); 
```

## PHPの例 {#section_ghf_gds_rz}

```
$collection = site->buildSidenotesCollection(title, articleId, url); 
```

## Pythonの例 {#section_dwg_gds_rz}

```
collection = site.build_sidenotes_collection(title, articleId, url) 
```

## ルビの例 {#section_enh_gds_rz}

```
collection = site.build_sidenotes_collection(title, articleId, url) 
```