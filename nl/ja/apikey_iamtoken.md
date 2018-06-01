---

copyright:
  years: 2018
lastupdated: "2018-05-09"

---


{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}

# API キーを使用した {{site.data.keyword.Bluemix_notm}} IAM トークンの取得方法
{: #iamtoken_from_apikey}

{{site.data.keyword.Bluemix}} API には、割り当てられた IAM 役割によって許可されたユーザーのみがアクセスできます。 したがって、API を呼び出すユーザーは、認証のために API 用の資格情報を渡す必要があります。 ここで説明するように、個人またはサービス ID の API キーを使用して、IAM トークンを生成できます。 このプロセスは、他の {{site.data.keyword.Bluemix_notm}} サービスと協力する必要があるアプリケーションを開発している場合にも使用されます。 サービス ID API キーを使用して、各 {{site.data.keyword.Bluemix_notm}} サービスに渡されるアクセス・トークンを取得する必要があります。

1. 次の `curl` コマンドを使用して、API キーを使用して IAM トークンを生成します。

### POST /identity/token

### ヘッダー:
  - Content-Type: application/x-www-form-urlencoded
  - Accept: application/json

### パラメーター:
  - grant_type=urn:ibm:params:oauth:grant-type:apikey
  - apikey=*[API キー]*

```
curl -k -X POST \
  --header "Content-Type: application/x-www-form-urlencoded" \
  --header "Accept: application/json" \
  --data-urlencode "grant_type=urn:ibm:params:oauth:grant-type:apikey" \
  --data-urlencode "apikey=<apikey>" \
  "https://iam.bluemix.net/identity/token"
```
{: codeblock}

以下の例は、予期される応答です。

### 応答:

```
{
  "access_token": "eyJhbGciOiJIUz......sgrKIi8hdFs",
  "refresh_token": "SPrXw5tBE3......KBQ+luWQVY=",
  "token_type": "Bearer",
  "expires_in": 3600,
  "expiration": 1473188353
}
```
{: codeblock}
