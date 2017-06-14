---

copyright:

  years: 2015, 2017
lastupdated: "2017-05-17"

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}

# Invitación a usuarios 
{: #iamuserinv}

Puede invitar a los usuarios de servicios de {{site.data.keyword.Bluemix_notm}}, aplicaciones e infraestructura de {{site.data.keyword.Bluemix_notm}} desde una sola ubicación. Para invitar a usuarios y gestionar invitaciones pendientes, debe ser propietario de cuenta o gestor de la organización o bien debe tener permisos de la infraestructura para añadir usuarios. Puede invitar a usuarios, cancelar invitaciones y volver a enviar una invitación pendiente a un usuario invitado. Puede invitar a un solo usuario o, si proporciona el mismo acceso para todos los miembros de un grupo de usuarios, puede invitar a varios usuarios a la vez.
{:shortdesc}

Complete los siguientes pasos para invitar a usuarios o para gestionar invitaciones de usuario en su cuenta: 

1. Desde la barra de menús, pulse **Gestionar** &gt; **Seguridad** &gt; **Identity & Access** &gt; **Usuarios**. La ventana Usuarios muestra una lista de los usuarios con sus direcciones de correo electrónico y el estado actual en las cuentas que gestiona. 
2. Pulse **Invitar usuarios**. 
3. Especifique la dirección de correo electrónico o el IBMid del usuario. Si proporciona el mismo acceso a varios usuarios, puede seleccionar **Invitar a varios usuarios** para especificar una lista de los usuarios a los que desea invitar. Separe las entradas de ID de usuario con comas. 
4. Añada una o varias de las opciones de acceso que gestionará. Debe asignar al menos una opción de acceso y configurar los valores para el usuario en cada opción de acceso que asigne. Para las opciones de acceso adicionales que no desee añadir y configurar, se asigna el valor predeterminado *no access* (sin acceso). Es posible que vea una o todas las opciones de acceso siguientes, en función de las opciones que está autorizado a gestionar: **Servicios habilitados de acceso e identidad**, **Acceso de Cloud Foundry**, **Acceso de infraestructura**.
Consulte [Asignación de acceso de usuario](/docs/iam/assignaccess.html) para obtener más información. 

Si determina que un usuario no necesita acceso, puede cancelar una invitación para cualquier usuario que se muestre en estado **Procesando** o **Pendiente** en la columna **Estado**. Si un usuario invitado no ha recibido una invitación, puede volver a enviar la invitación a cualquier usuario en estado **Pendiente**.  
