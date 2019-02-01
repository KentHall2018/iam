---

copyright:

  years: 2015, 2018
lastupdated: "2018-11-30"

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}

# Gestión de claves de API de usuario
{: #userapikey}

Un usuario federado o no federado puede crear una clave de API para utilizarla en la CLI o como parte de la automatización para iniciar sesión con su identidad de usuario. Puede utilizar la IU o la CLI para gestionar sus claves de API listando sus claves, creando claves, actualizando claves o suprimiendo claves. Para gestionar las claves de API de {{site.data.keyword.Bluemix_notm}} asociadas a su identidad de usuario, vaya a **Gestionar** &gt; **Acceso (IAM)** y seleccione **Usuarios**. Luego pulse el nombre en la lista y seleccione la opción **Detalles de usuario** para ver una lista de sus claves de API con descripciones y fechas. A continuación, puede crear, editar o suprimir claves de API. Y, para obtener una lista completa de mandatos de CLI disponibles, consulte [`ibmcloud iam api-keys`](/docs/cli/reference/ibmcloud/cli_api_policy.html#ibmcloud_iam_api_keys).

Como [usuario federado](/docs/account/adminpublic.html#federatedid), puede utilizar una clave de API para iniciar una sesión mediante la variable de entorno `IBMCLOUD_API_KEY`. Para obtener más información sobre el uso de una clave de API para iniciar sesión, consulte [Inicio de sesión con un ID federado](/docs/cli/login_federated_id.html#federated_id).
{:shortdesc}

## Creación de una clave de API

Como usuario de {{site.data.keyword.Bluemix_notm}}, podría desear utilizar una clave de API al habilitar un programa o script sin distribuir su contraseña al script. Otra ventaja en la utilización de una clave de API, es que un usuario o una organización pueden crear varias claves de API para distintos programas y que es posible suprimirlas de forma independiente si están en riesgo sin interferir con otras claves de API o incluso el usuario. Puede crear hasta 20 claves de API.

Para crear una clave de API para la identidad de usuario en la IU, siga estos pasos:

1. Vaya a **Gestionar** &gt; **Acceso (IAM)** y seleccione **Usuarios**. Luego pulse el nombre en la lista y seleccione la opción **Detalles de usuario**.
2. Pulse **Crear una clave de API de {{site.data.keyword.Bluemix_notm}}**.
3. Especifique un nombre y una descripción para su clave de API.
4. Pulse **Crear**.
5. A continuación, pulse **Mostrar** para visualizar, copiar y guardar la clave de API para más tarde, o pulse **Descargar**.

Por motivos de seguridad, la clave de API sólo está disponible para copiarse o descargarse en el momento de la creación. Si se pierde la clave de API, deberá crear una nueva clave de API.
{: tip}

Para crear una clave de API mediante la CLI, utilice el mandato siguiente:

1. Escriba `ibmcloud iam api-key-create NAME [-d DESCRIPTION] [-f, --file FILE]` en el indicador de mandatos, y especifique un nombre, una descripción y un archivo para guardar la clave. Observe el ejemplo siguiente:

```
ibmcloud iam api-key-create MyKey -d "this is my API key" --file key_file
```


## Actualización de una clave de API

Si desea cambiar el nombre o la descripción de una clave de API, lleve a cabo los pasos siguientes en la IU o CLI.

Para editar una clave de API, siga estos pasos:

1. Vaya a **Gestionar** &gt; **Acceso (IAM)** y seleccione **Usuarios**. Luego pulse el nombre en la lista y seleccione la opción **Detalles de usuario**.
2. Identifique la fila de la clave de API que desea actualizar y seleccione **Editar** en el menú **Acciones** ![Icono Lista de acciones](../icons/action-menu-icon.svg).
3. Actualice la información de su clave de API.
4. Pulse **Aplicar**.

Para editar una clave de API mediante la CLI, especifique el mandato siguiente:

1. Escriba `ibmcloud iam api-key-update NAME [-n NAME] [-d DESCRIPTION]` en el indicador de mandatos, especificando el nombre antiguo, el nombre nuevo y una descripción nueva para la clave. Por ejemplo:

```
ibmcloud iam api-key-update MyCurrentName -n MyNewName -d "la nueva descripción de mi clave"
```

## Bloqueo de una clave de API

Para las claves de API de plataforma que representan la identidad de usuario, puede impedir que la clave de API se suprima al bloquearla. Una clave de API bloqueada está indicada mediante el icono ![icono Bloqueado](images/locked.svg "Bloqueado"). Puede bloquear y desbloquear su clave de API mediante la IU o la CLI.

### Bloqueo y desbloqueo de una clave de API desde la IU

1. Vaya a **Gestionar** &gt; **Acceso (IAM)** y seleccione **Usuarios**. Luego pulse el nombre en la lista y seleccione la opción **Detalles de usuario**.
2. Identifique la fila de la clave de API que desea bloquear y seleccione **Bloquear** en el menú **Acciones** ![Icono Lista de acciones](../icons/action-menu-icon.svg).

Puede desbloquear su clave de API en cualquier momento para actualizar o eliminar la clave de API de la cuenta. Seleccione en la tabla la clave de API que desea desbloquear y seleccione **Desbloquear** en el menú **Acciones** ![Icono Lista de acciones](../icons/action-menu-icon.svg).
{: tip}

### Bloqueo y desbloqueo de una clave de API mediante la CLI

Para bloquear una clave de API, utilice el mandato siguiente:

```
ibmcloud iam api-key-lock (NAME|UUID) [-f, --force]
```

<strong>Requisitos previos</strong>: Punto final, Inicio de sesión

<strong>Opciones de mandato</strong>:
<dl>
<dt>NAME (necesario)</dt>
<dd>Nombre de la clave de API a bloquear, exclusiva con UUID.</dd>
<dt>UUID (necesario)</dt>
<dd>UUID de la clave de API a bloquear, exclusiva con NAME.</dd>
<dt>-f, --force</dt>
<dd>Fuerza el bloqueo sin confirmación.</dd>
</dl>

<strong>Ejemplo</strong>:

Bloquear clave de API `test-api-key`

```
ibmcloud iam api-key-lock test-api-key
```

Para desbloquear una clave de API, ejecute el mandato siguiente:

```
ibmcloud iam api-key-unlock (NAME|UUID) [-f, --force]
```

<strong>Requisitos previos</strong>: Punto final, Inicio de sesión

<strong>Opciones de mandato</strong>:
<dl>
<dt>NAME (necesario)</dt>
<dd>Nombre de la clave de API a desbloquear, exclusiva con UUID.</dd>
<dt>UUID (necesario)</dt>
<dd>UUID de la clave de API a desbloquear, exclusiva con NAME.</dd>
<dt>-f, --force</dt>
<dd>Fuerza el desbloqueo sin confirmación.</dd>
</dl>

<strong>Ejemplo</strong>:

Desbloquear la clave de API `test-api-key`

```
ibmcloud iam api-key-unlock test-api-key
```


## Supresión de una clave de API

Si está utilizando una estrategia de rotación de clave, es posible que desee suprimir una clave más antigua y sustituirla por una clave nueva.

Para suprimir una clave de API, siga estos pasos:

1. Vaya a **Gestionar** &gt; **Acceso (IAM)** y seleccione **Usuarios**. Luego pulse el nombre en la lista y seleccione la opción **Detalles de usuario**.
2. Identifique la fila de la clave de API que desea suprimir y seleccione **Suprimir** en el menú **Acciones** ![Icono Lista de acciones](../icons/action-menu-icon.svg).
3. A continuación, confirme la supresión pulsando **Suprimir**.

Para suprimir una clave de API con la CLI:
1. Escriba `ibmcloud iam api-key-delete NAME` en el indicador de mandatos, especificando el nombre de la clave a suprimir.
