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

# Come ottenere un token IAM {{site.data.keyword.Bluemix_notm}} utilizzando una chiave API 
{: #iamtoken_from_apikey}

Alle API {{site.data.keyword.Bluemix}} possono accedere solo gli utenti autorizzati da un ruolo IAM assegnato. Pertanto, l'utente che richiama l'API deve passare le credenziali per l'autenticazione da parte dell'API. Puoi generare un token IAM utilizzando la chiave API tua personale o dell'ID servizio, come descritto qui. Questo processo è utilizzato anche se stai sviluppando un'applicazione che deve lavorare con altri servizi {{site.data.keyword.Bluemix_notm}}. Devi utilizzare una chiave API dell'ID servizio per ottenere un token di accesso da passare a ciascuno dei servizi {{site.data.keyword.Bluemix_notm}}.

1. Utilizza il seguente comando `curl` per generare un token IAM utilizzando una chiave API.

### POST /identity/token

### Intestazioni
  - Content-Type: application/x-www-form-urlencoded
  - Accept: application/json

### Parametri
  - grant_type=urn:ibm:params:oauth:grant-type:apikey
  - apikey=*[Api key]*

```
curl -k -X POST \
  --header "Content-Type: application/x-www-form-urlencoded" \
  --header "Accept: application/json" \
  --data-urlencode "grant_type=urn:ibm:params:oauth:grant-type:apikey" \
  --data-urlencode "apikey=<apikey>" \
  "https://iam.bluemix.net/identity/token"
```
{: codeblock}

Il seguente esempio è la risposta prevista:

### Risposta

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
