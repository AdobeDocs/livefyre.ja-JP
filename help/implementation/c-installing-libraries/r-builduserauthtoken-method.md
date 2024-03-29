---
description: 呼び出し元のネットワークに対して、暗号化されたユーザー認証トークンを返します。
title: buildUserAuthTokenネットワークメソッド
exl-id: dcc61c4b-90d9-42a0-9f46-73a843a4ad78
translation-type: tm+mt
source-git-commit: a2449482e617939cfda7e367da34875bf187c4c9
workflow-type: tm+mt
source-wordcount: '85'
ht-degree: 8%

---

# buildUserAuthTokenネットワークメソッド{#builduserauthtoken-network-method}

呼び出し元のネットワークに対して、暗号化されたユーザー認証トークンを返します。

| 変数 | タイプ | 説明 |
|--- |--- |--- |
| userId | 文字列 | このトークンが属するユーザーのユーザーID。 |
| displayName | 文字列 | ユーザーの表示名です。 |
| expires | 二重 | トークンの有効期限（秒）。 |

## Javaの例{#section_nyl_ycs_rz}

```
network.buildUserAuthToken(userId, displayName, expires); 
```

出力例：

```
eyJhbGciOiJIUzI1NiJ9.eyJkb21haW4iOiJ0ZXN0LmZ5cmUuY29tIiwidXNlcl9pZCI6InN5c3RlbSIsImRpc3BsYXlfbmFtZSI6InN5c3RlbSIsImV4cGlyZXMiOjEzOTY2NTUwODN9.33GuJF_ou2O6CCV22Y3PlLUgP2Igy9vAXfmLONkt-Yo 
```

## NodeJSの例{#section_xkd_gds_rz}

```
network.buildUserAuthToken(userId, displayName, expires); 
```

出力例：

```
eyJhbGciOiJIUzI1NiJ9.eyJkb21haW4iOiJ0ZXN0LmZ5cmUuY29tIiwidXNlcl9pZCI6InN5c3RlbSIsImRpc3BsYXlfbmFtZSI6InN5c3RlbSIsImV4cGlyZXMiOjEzOTY2NTUwODN9.33GuJF_ou2O6CCV22Y3PlLUgP2Igy9vAXfmLONkt-Yo 
```

## PHPの例{#section_ghf_gds_rz}

```
$network->buildUserAuthToken(userId, displayName, expires); 
```

出力例：

```
eyJhbGciOiJIUzI1NiJ9.eyJkb21haW4iOiJ0ZXN0LmZ5cmUuY29tIiwidXNlcl9pZCI6InN5c3RlbSIsImRpc3BsYXlfbmFtZSI6InN5c3RlbSIsImV4cGlyZXMiOjEzOTY2NTUwODN9.33GuJF_ou2O6CCV22Y3PlLUgP2Igy9vAXfmLONkt-Yo
```

## Pythonの例{#section_dwg_gds_rz}

```
network.build_user_auth_token(userId, displayName, expires) 
```

出力例：

```
eyJhbGciOiJIUzI1NiJ9.eyJkb21haW4iOiJ0ZXN0LmZ5cmUuY29tIiwidXNlcl9pZCI6InN5c3RlbSIsImRpc3BsYXlfbmFtZSI6InN5c3RlbSIsImV4cGlyZXMiOjEzOTY2NTUwODN9.33GuJF_ou2O6CCV22Y3PlLUgP2Igy9vAXfmLONkt-Yo
```

## Rubyの例{#section_enh_gds_rz}

```
network.build_user_auth_token(userId, displayName, expires) 
```

出力例：

```
eyJhbGciOiJIUzI1NiJ9.eyJkb21haW4iOiJ0ZXN0LmZ5cmUuY29tIiwidXNlcl9pZCI6InN5c3RlbSIsImRpc3BsYXlfbmFtZSI6InN5c3RlbSIsImV4cGlyZXMiOjEzOTY2NTUwODN9.33GuJF_ou2O6CCV22Y3PlLUgP2Igy9vAXfmLONkt-Yo
```
