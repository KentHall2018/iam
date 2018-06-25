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

# 创建和使用服务标识
{: #serviceids}

服务标识用于标识服务或应用程序，类似于用户标识对用户进行标识的方式。创建的服务标识可用于支持 {{site.data.keyword.Bluemix_notm}} 外部的应用程序访问 {{site.data.keyword.Bluemix_notm}} 服务。您可以向服务标识分配特定访问策略，以限制使用特定服务的许可权，甚至可以将访问不同服务的许可权组合在一起。由于服务标识并不与特定用户绑定，因此即使用户离开组织并将其从帐户中删除，该服务标识仍会保留，以确保您的应用程序或服务保持正常运行。

创建服务标识时，将创建唯一的名称和描述，方便您在 UI 中识别和使用。一旦创建了服务标识，就可以创建特定于每个服务标识的 API 密钥，应用程序可以使用这些密钥向 {{site.data.keyword.Bluemix_notm}} 服务进行认证。要确保应用程序具有对 {{site.data.keyword.Bluemix_notm}} 服务进行认证的相应访问权，您可使用分配给所创建的每个服务标识的访问策略。 

与服务标识关联的访问策略支持在该服务标识用于访问特定服务时可以执行的特定操作。可以为单个服务标识分配多个策略，这些策略定义访问多个支持身份和访问权的服务时允许的访问级别。例如，您有两个服务，每个服务分别有两个服务实例。您可为一个服务的所有可用实例分配`查看者`角色，而仅为第二个服务的一个实例分配`编辑者`角色。这样，就可以定制对多个服务的访问权，但仍使用单个 API 密钥向所有这些服务进行认证。


## 创建服务标识

要创建服务标识，请转至**管理** &gt; **安全性** &gt; **身份和访问权**，然后选择**服务标识**。执行为服务标识创建名称和描述的过程。然后，使用**操作**菜单来管理服务标识。您可以首先分配策略和创建 API 密钥。有关使用 API 密钥的更多信息，请参阅[管理服务标识 API 密钥](/docs/iam/serviceid_keys.html#serviceidapikeys)。 

## 更新服务标识

您可以随时通过更改服务标识的名称和描述来更新该服务标识。还可以根据需要删除和创建新的 API 密钥，或更新分配的访问策略。但是，对现有服务标识进行的任何更改（例如，更改分配的策略或删除当前正在使用的 API 密钥）可能会导致使用该服务标识的应用程序发生服务中断。

## 锁定服务标识

为了避免因删除服务标识而给服务的用户造成停机或中断的情况，您可以选择使用 UI 或 CLI 锁定服务标识。锁定服务标识还可以防止变更、删除或分配任何访问策略，以及创建或删除与服务标识相关联的任何 API 密钥。除了有能力锁定服务标识外，还可以[锁定单个 API 密钥](/docs/iam/serviceid_keys.html#lockkey)（与帐户中每个服务标识关联的 API 密钥）。 

无法删除锁定的服务标识，也无法更新访问策略。但是，锁定的服务标识仍然可以从它们添加到的任何访问组中除去。这意味着从访问组中除去服务标识时，将除去该访问组中通过其成员资格分配给该标识的任何访问权。
{: tip}

### 提供锁定服务标识所需的用户访问权

为了使用户有权锁定和解锁服务标识以及与服务标识关联的 API 密钥，必须为其分配特定的访问策略。两种类型的访问策略可以授予相应的访问权：

* 对帐户中所有服务标识的访问权
* 对帐户中特定服务标识的访问权

要分配对帐户中所有服务标识的访问权，请使用以下详细信息来设置访问策略：

* “编辑者”或“管理员”角色 
* IAM 身份服务 

要分配对帐户中特定服务标识的访问权，请使用以下详细信息来设置访问策略：

* “编辑者”或“管理员”角色
* IAM 身份服务 
* 在**资源类型**字段中指定 `serviceid` 
* 在**资源标识**字段中指定服务标识的标识

要获取特定服务标识的标识，请转至**管理** > **安全性** > **身份和访问权**，然后选择**服务标识**。确定要查看其详细信息的服务标识，然后复制标识值。
{: tip}

### 在 UI 中锁定服务标识

锁定的服务标识由 ![“已锁定”图标](images/locked.svg "已锁定") 图标指示。

1. 在菜单栏中，单击**管理** &gt; **安全性** &gt; **身份和访问权**，然后选择**服务标识**。
2. 确定要锁定的服务标识所在的行，然后从**操作**菜单中选择**锁定服务标识**。

要解锁服务标识，请从表中选择要解锁的服务标识，然后从**操作**菜单中选择**解锁服务标识**。您必须具有解锁服务标识所需的相应访问级别。
{: tip}

### 使用 CLI 锁定和解锁服务标识

要锁定服务标识，请使用以下命令：

```
ibmcloud iam service-id-lock (NAME|UUID) [-f, --force]
```

命令选项：

<dl>
  <dt>NAME（必需）</dt>
  <dd>服务的名称，与 UUID 互斥</dd>
  <dt>UUID（必填）</dt>
  <dd>服务的 UUID，与 NAME 互斥</dd>
  <dt>-f, --force</dt>
  <dd>锁定而不确认</dd>
</dl>

<strong>示例</strong>：

锁定服务标识 `sample-test` 而不确认

```
ibmcloud iam service-id-lock sample-test -f
```

锁定服务标识 `ServiceId-cb258cb9-8de3-4ac0-9aec-b2b2d27ac976`

```
ibmcloud iam service-id-lock ServiceId-cb258cb9-8de3-4ac0-9aec-b2b2d27ac976
```

要解锁服务标识，请使用以下命令：

 ```
ibmcloud iam service-id-unlock (NAME|UUID) [-f, --force]
```

命令选项：

<dl>
  <dt>NAME（必需）</dt>
  <dd>服务的名称，与 UUID 互斥</dd>
  <dt>UUID（必填）</dt>
  <dd>服务的 UUID，与 NAME 互斥</dd>
  <dt>-f, --force</dt>
  <dd>解锁而不确认</dd>
</dl>

<strong>示例</strong>：锁定服务标识 `sample-test` 而不确认

```
ibmcloud iam service-id-unlock sample-test -f
```

解锁服务标识 `ServiceId-cb258cb9-8de3-4ac0-9aec-b2b2d27ac976`

```
ibmcloud iam service-id-unlock ServiceId-cb258cb9-8de3-4ac0-9aec-b2b2d27ac976
```



## 如何使用服务标识的示例

下面是如何将服务标识与 {{site.data.keyword.objectstorageshort}} 和 Cloud SQL 查询服务配合使用的示例。

- {{site.data.keyword.objectstorageshort}} - [入门](/docs/services/cloud-object-storage/getting-started-cli.html#getting-started-cli-).
- Cloud SQL Query - [如何使用 SQL Query REST API ![外部链接图标](../icons/launch-glyph.svg)](https://www.youtube.com/embed/s6S4AdJItHk?rel=0){: new_window}.

