---

copyright:

  years: 2017, 2018
  
lastupdated: "2018-06-01"

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:tip: .tip}

# 建立及使用服務 ID
{: #serviceids}

服務 ID 會識別與使用者 ID 如何識別使用者類似的服務或應用程式。您建立的服務 ID 可以用來在 {{site.data.keyword.Bluemix_notm}} 外部啟用應用程式，以存取您的 {{site.data.keyword.Bluemix_notm}} 服務。您可以將特定存取原則指派給服務 ID，而服務 ID 限制用於使用特定服務的許可權，或甚至結合用於存取不同服務的許可權。因為服務 ID 未關聯至特定使用者，所以如果使用者離開組織，並已從帳戶中予以刪除，則服務 ID 仍可確保您的應用程式或服務保持啟動並執行。

當您建立服務 ID 時，會建立唯一名稱及說明，方便您在使用者介面中識別及使用服務。在您建立服務 ID 之後，即可建立每一個服務 ID 特有的 API 金鑰，而應用程式可以使用這些金鑰向 {{site.data.keyword.Bluemix_notm}} 服務進行鑑別。若要確定應用程式具有向 {{site.data.keyword.Bluemix_notm}} 服務進行鑑別的適當存取權，請使用指派給所建立之每一個服務 ID 的存取原則。 

與服務 ID 相關聯的存取原則會啟用可在使用該服務 ID 存取特定服務時採取的特定動作。單一服務 ID 可獲指派多個原則，以定義在存取多個啟用「身分及存取」的服務時，所容許的存取層次。例如，您有兩個服務，各有兩個服務實例。例如，您可能針對一個服務的所有可用實例指派 `Viewer` 角色，並針對第二個服務的一個實例僅指派 `Editor` 角色。因此，您可以自訂多個服務的存取權，但使用單一 API 金鑰來鑑別所有服務。


## 建立服務 ID

若要建立服務 ID，請移至**管理** &gt; **安全** &gt; **身分及存取**，然後選取**服務 ID**。請遵循可建立服務 ID 之名稱及說明的處理程序。然後，使用**動作**功能表來管理您的服務 ID。您可以從指派原則以及建立 API 金鑰開始。如需使用 API 金鑰的相關資訊，請參閱[管理服務 ID API 金鑰](/docs/iam/serviceid_keys.html#serviceidapikeys)。 

## 更新服務 ID

您隨時可以變更名稱及說明，來更新服務 ID。也可以視需要刪除及建立新的 API 金鑰，或更新所指派的存取原則。不過，您對現有服務 ID 進行的任何變更（例如，變更已指派的原則，或刪除目前正在使用的 API 金鑰），可能會導致使用該服務 ID 之應用程式的服務岔斷。

## 鎖定服務 ID

為了避免因為刪除服務 ID 而導致服務的使用者運行中斷或岔斷，您可以選擇利用使用者介面或 CLI 來鎖定服務 ID。鎖定服務 ID 也可以防止變更、刪除或指派任何存取原則，以及防止建立或刪除與服務 ID 相關聯的任何 API 金鑰。除了可以鎖定服務 ID 之外，您還可以[鎖定與帳戶中每個服務 ID 相關聯的個別 API 金鑰](/docs/iam/serviceid_keys.html#lockkey)。 

已鎖定的服務 ID 無法刪除，且存取原則無法更新。不過，還是可以將已鎖定的服務 ID 從其新增到的任何存取群組中移除。這表示，將服務 ID 從存取群組中移除時，依 ID 在存取群組中的成員資格指派給 ID 的任何存取權都會移除。
{: tip}

### 提供使用者鎖定服務 ID 的存取權

若要讓使用者有鎖定和解除鎖定服務 ID 的存取權，以及存取與服務 ID 相關聯的 API 金鑰，必須為他們指派特定的存取原則。有兩種存取原則類型可以授與適當的存取權：

* 帳戶中所有服務 ID 的存取權
* 帳戶中特定服務 ID 的存取權

若要指派帳戶中所有服務 ID 的存取權，請設定具有下列詳細資料的存取原則：

* 「編輯者」或「管理者」角色 
* IAM 身分服務

若要指派帳戶中特定服務 ID 的存取權，請設定具有下列詳細資料的存取原則：

* 「編輯者」或「管理者」角色
* IAM 身分服務
* 在**資源類型**欄位中指定 `serviceid` 
* 在**資源 ID** 欄位中指定服務 ID 識別碼

若要取得特定服務 ID 的識別碼，請移至**管理** > **安全** > **身分及存取**，然後選取**服務 ID**。選取您要檢視其詳細資料的服務 ID，並複製 ID 值。
{: tip}

### 從使用者介面鎖定服務 ID

已鎖定的服務 ID 會以 ![「已鎖定」圖示](images/locked.svg "已鎖定") 圖示來表示。

1. 從功能表列中按一下**管理** &gt; **安全** &gt; **身分及存取**，然後選取**服務 ID**。
2. 識別您要鎖定的服務 ID 列，然後從**動作**功能表中選取**鎖定服務 ID**。

若要解除鎖定服務 ID，請從表格中選取您要解除鎖定的服務 ID，然後從**動作**功能表中選取**解除鎖定服務 ID**。您必須要有適當的存取層次，才能解除鎖定服務 ID。
{: tip}

### 使用 CLI 來鎖定及解除鎖定服務 ID

若要鎖定服務 ID，請使用下列指令：

```
ibmcloud iam service-id-lock (NAME|UUID) [-f, --force]
```

指令選項：

<dl>
  <dt>NAME（必要）</dt>
  <dd>服務的名稱，不能與 UUID 同時使用</dd>
  <dt>UUID（必要）</dt>
  <dd>服務的 UUID，不能與 NAME 同時使用</dd>
  <dt>-f, --force</dt>
  <dd>鎖定而不進行確認</dd>
</dl>

<strong>範例</strong>：

鎖定服務 ID `sample-test`，而不進行確認

```
ibmcloud iam service-id-lock sample-test -f
```

鎖定服務 ID `ServiceId-cb258cb9-8de3-4ac0-9aec-b2b2d27ac976`

```
ibmcloud iam service-id-lock ServiceId-cb258cb9-8de3-4ac0-9aec-b2b2d27ac976
```

若要解除鎖定服務 ID，請使用下列指令：

 ```
ibmcloud iam service-id-unlock (NAME|UUID) [-f, --force]
```

指令選項：

<dl>
  <dt>NAME（必要）</dt>
  <dd>服務的名稱，不能與 UUID 同時使用</dd>
  <dt>UUID（必要）</dt>
  <dd>服務的 UUID，不能與 NAME 同時使用</dd>
  <dt>-f, --force</dt>
  <dd>解除鎖定而不進行確認</dd>
</dl>

<strong>範例</strong>：

解除鎖定服務 ID `sample-test`，而不進行確認

```
ibmcloud iam service-id-unlock sample-test -f
```

解除鎖定服務 ID `ServiceId-cb258cb9-8de3-4ac0-9aec-b2b2d27ac976`

```
ibmcloud iam service-id-unlock ServiceId-cb258cb9-8de3-4ac0-9aec-b2b2d27ac976
```



## 服務 ID 的用法範例

下列範例說明服務 ID 與 {{site.data.keyword.objectstorageshort}} 及 Cloud SQL Query 服務如何搭配使用。

- {{site.data.keyword.objectstorageshort}} - [開始使用](/docs/services/cloud-object-storage/getting-started-cli.html#getting-started-cli-)。
- Cloud SQL Query - [How to use the SQL Query REST API ![External link icon](../icons/launch-glyph.svg)](https://www.youtube.com/embed/s6S4AdJItHk?rel=0){: new_window}。

