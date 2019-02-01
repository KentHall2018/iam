---

copyright:

  years: 2017, 2018

lastupdated: "2018-11-30"

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:tip: .tip}
{:note: .note}

# Guía de aprendizaje de iniciación
{: #getstarted}

Esta guía de aprendizaje está pensada para ayudarle a preparar y ejecutar rápidamente con IBM Cloud Identity and Access Management (IAM) invitando usuarios a su cuenta y asignándoles acceso de Cloud IAM.
{:shortdesc}

Esta guía de aprendizaje es para recursos habilitados para IAM. Para los servicios que no permite la creación de políticas IAM de nube para gestionar el acceso, puede utilizar el [acceso de Cloud Foundry](/docs/iam/cfaccess.html#cfaccess) o los [permisos de la infraestructura clásica](/docs/iam/infrastructureaccess.html#infrapermission).
{: note}


## Paso 1. Invitar a usuarios y asignar acceso inicial

Puede invitar a uno o varios usuarios y establecer una política de acceso inicial para los usuarios en la invitación. Si invita varios usuarios en una invitación se asigna el mismo acceso a todos ellos. En la sección de acceso de la página Invitar a usuarios, solo verá las secciones que puede asignar.

Como propietario de cuenta, puede asignar roles de Cloud IAM a los usuarios que invite en la sección Servicios. Puede proporcionar acceso a todos los recursos de un grupo de recursos, a todos los recursos para un servicio específico de un grupo de recursos, a todos los servicios habilitados para Identity and Access en la cuenta, a un solo recurso de la cuenta o acceso a los servicios de gestión de cuentas:

1. Vaya a **Gestionar** &gt; **Acceso (IAM)** y seleccione **Usuarios**.
2. Pulse **Invitar a usuarios**.
3. Especifique la dirección de correo electrónico de los usuarios que desee invitar.
4. En la sección **Acceso**, expanda la opción **Servicios**.
5. Elija si desea asignar acceso a un **Recurso**, a los recursos de un **Grupo de recursos** o a los **Servicios de gestión de cuentas**.
6. En función de su selección, siga las indicaciones para especificar el acceso deseado. Si ha seleccionado la opción del grupo de recursos, también debe proporcionar el usuario con acceso para ver, editar o gestionar el acceso al grupo de recursos seleccionando un rol para acceder al grupo de recursos.
7. Si tiene permisos, también puede asignar acceso de Cloud Foundry o de infraestructura en la invitación.
8. Pulse **Invitar a usuarios**.

Para obtener más información, consulte [Invitación de usuarios y asignación de acceso](/docs/iam/iamuserinv.html#iamuserinv).

## Paso 2. Crear grupos de acceso

Para agilizar el proceso de asignación de acceso a los usuarios de su cuenta, puede crear grupos de acceso. Los grupos de usuarios constituyen una manera de organizar usuarios e ID de servicio a los que luego puede asignar acceso fácilmente mediante la definición de una sola política para todo el grupo.

### Configurar los grupos

Para crear un grupo de acceso, complete los pasos siguientes:

1. En la barra de menús, pulse **Gestionar** &gt; **Acceso (IAM)** y seleccione **Grupos de acceso**.
2. Pulse **Crear**.
3. Escriba un nombre y una descripción opcional para el grupo
4. Pulse **Crear**.

A continuación, siga configurando el grupo añadiendo usuarios o ID de servicio:

1. Seleccione el nombre del grupo al que desea añadir.
2. Pulse **Añadir usuarios**.
3. Seleccione los usuarios de la lista que desea añadir y pulse **Añadir a grupo**.
4. Para añadir ID de servicio al grupo, pulse **ID de servicio**.
5. Seleccione los ID de la lista que desea añadir y pulse **Añadir grupo**.

### Asignar acceso a los grupos

Después de crear los grupos, puede asignar acceso a todas las entidades del grupo con una sola política o con varias políticas.

1. En la barra de menús, pulse **Gestionar** &gt; **Acceso (IAM)** y seleccione **Grupos de acceso**.
2. Seleccione el nombre del grupo al que desea asignar el acceso.
3. En el separador **Políticas de acceso**, pulse **Asignar acceso** para configurar una política de acceso. Repita este paso las veces que necesita para asignar más acceso.

Al organizar recursos en grupos de recursos y usuarios en grupos de acceso, puede asignar a un grupo de usuarios el acceso a un grupo de recursos con una sola política, lo que reduce el número total de políticas que debe gestionar.
{: tip}


## Paso 3. Gestionar el acceso de usuarios existentes

Después de invitar a usuarios, asignar el acceso inicial y crear grupos de acceso, es posible que desee asignar más acceso o editar el acceso inicial asignado para garantizar que todos los usuarios y grupos de su cuenta tienen el nivel de acceso deseado.

### Asignación de nuevos accesos

Para asignar una nueva política de acceso, siga los pasos siguientes:

1. En la barra de menús, pulse **Gestionar** &gt; **Acceso (IAM)** y seleccione **Usuarios**.
2. Seleccione el nombre del usuario al que desea asignar el acceso.
3. Pulse **Políticas de acceso**.
4. Pulse **Asignar acceso**.
5. Elija la forma de asignar el acceso:
    * Seleccione **Asignar acceso dentro de un grupo de recursos** para asignar acceso a todos los recursos dentro de un grupo o solo a los recursos de un servicio específico dentro de un grupo. También debe proporcionar el usuario con acceso para ver, editar o gestionar el acceso al grupo de recursos seleccionando un rol para acceder al grupo de recursos. Seleccione **Sin acceso** si desea que el usuario solo tenga acceso al recurso especificado y no al grupo en el que está organizado.
    * Seleccione **Asignar acceso a recursos** para asignar acceso a todos los recursos habilitados para identificación y acceso en la cuenta, a todos los recursos de un servicio específico en la cuenta, a una única instancia o a un único recurso dentro de una instancia de servicio específica.
    * Seleccione **Asignar acceso a servicios de gestión de cuentas** para asignar acceso a todos los servicios de gestión de cuentas o solo a un servicio de gestión de cuentas.
5. Seleccione cualquier combinación de roles para definir el ámbito del acceso. Para obtener más información, consulte [Roles de Cloud IAM](/docs/iam/users_roles.html#iamusermanrol).
6. Pulse **Asignar**.


### Edición de accesos existentes

Puede actualizar los accesos existentes editando los roles asignados a un usuario.

1. En la barra de menús, pulse **Gestionar** &gt; **Acceso (IAM)** y seleccione **Usuarios**.
2. Seleccione el nombre del usuario para el que desea editar el acceso.
3. Pulse **Políticas de acceso**.
4. Pulse **Editar** en el menú **Acciones** ![Icono Lista de acciones](../icons/action-menu-icon.svg) en la fila correspondiente a la política que desea editar.
4. Edite la política actualizando los roles asignados.
5. Pulse **Guardar**.

También puede eliminar el acceso de un usuario pulsando la opción **Eliminar** en el menú **Acciones** ![Icono Lista de acciones](../icons/action-menu-icon.svg) correspondiente a la política que desea eliminar.

## Pasos siguientes

Aprenda qué más puede realizar con Cloud IAM echando un vistazo a la lista de [Características de Cloud IAM](/docs/iam/index.html#features).
