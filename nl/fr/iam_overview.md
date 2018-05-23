---

copyright:

  years: 2017, 2018

lastupdated: "2018-04-02"

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}

# Concepts IAM
{: #iamconcepts}

## Identité

Dans {{site.data.keyword.Bluemix_notm}} IAM, le concept d'identité recouvre les éléments suivants :

<dl>
<dt>Identités des utilisateurs</dt>
<dd>Tous les utilisateurs sont identifiés par leur IBMid.</dd>
<dt>Identités des services et des applications</dt>
<dd>Les ID de service sont la fonctionnalité Cloud IAM utilisée pour fournir une identité distincte aux services et aux applications. Vous pouvez créer un ID de service qu'utilisera une application pour accéder à vos services {{site.data.keyword.Bluemix_notm}} de sorte que les données d'identification d'un utilisateur individuel n'ont pas à être utilisées.</dd>
<dt>Clés d'API</dt>
<dd>Cloud IAM fournit des clés d'API de plateforme que vous pouvez utiliser pour vous authentifier via l'API ou l'interface de ligne de commande comme ID utilisateur ou de service. Etant donné que ces clés d'API sont fournies par le biais de Cloud IAM, elle ne peuvent pas être utilisées de façon générale pour s'authentifier avec un IBMid en dehors d'IBM Cloud. </dd>
<dt>Ressources</dt>
<dd>Les ressources {{site.data.keyword.Bluemix_notm}} sont identifiées par leur nom de ressource de cloud. Pour plus d'informations, voir [Noms de ressource de cloud](/docs/overview/crn.html#crn).</dd>
</dl>

## Gestion des accès

Dans {{site.data.keyword.Bluemix_notm}}, le concept de gestion des accès concerne un petit nombre de composants interdépendants, incluant les utilisateurs, les ressources, les règles, les rôles, les actions et le système de contrôle Cloud IAM, qui autorise des utilisateurs à effectuer des actions sur des ressources au sein d'un compte.

Vous pouvez passer en revue la liste suivante pour en savoir plus sur ces composants Cloud IAM :

<dl>
<dt>Utilisateurs</dt>
<dd>Tous les utilisateurs d'un compte sont identifiés par leur IBMid. Des utilisateurs peuvent être invités dans le compte et se voir accorder l'accès à des ressources. L'accès peut être affecté à des ressources individuelles, jusqu'au niveau instance, ou à un ensemble de ressources organisées dans un groupe de ressources du compte.</dd>
<dt>Groupe d'accès</dt>
<dd>Un groupe d'utilisateurs et d'ID de service peut être créé par le propriétaire de compte de sorte que le même accès puisse être affecté à toutes les entités au sein du groupe au moyen d'une seule règle.</dd>
<dt>Ressources</dt>
<dd>Les ressources d'un compte sont les offres de service mises à disposition, sélectionnées dans le catalogue, ou des ressources à granularité plus fine au sein d'une instance de service.</dd>
<dt>Règles</dt>
<dd>Les règles définissent comment sont accordés à des ID utilisateur ou de service du compte des droits d'accès à des ressources du compte. Les règles incluent un objet, une cible et un rôle. L'objet correspond à l'ID utilisateur ou de service auquel vous accordez l'accès. La cible de la règle est la ressource à laquelle vous voulez accorder l'accès. Et les rôles permettent de définir le niveau d'accès ou les actions autorisées sur la cible de la règle. Il existe trois types de règle permettant d'accorder l'accès à des ressources de compte : règle de groupe de ressources, règle d'instance de ressource et règle de niveau compte pour l'accès à tous les services Identity and Access activés. Selon vos sélections, vous disposez d'options de configuration personnalisée, par exemple, définir l'accès descendant à des ressources d'une région spécifique ou définir l'accès au niveau granulaire d'une ressource propre à un service d'une instance.</dd>
<dt>Rôles</dt>
<dd>Les rôles d'accès Cloud IAM permettent à un utilisateur d'effectuer des tâches spécifiques sur la ressource définie dans la règle. Il existe deux types de rôle d'accès : gestion de plateforme et accès à un service. Les rôles de gestion de plateforme définissent les actions autorisées de gestion des ressources au niveau de la plateforme, par exemple, l'accès utilisateur, la création d'ID d'instance et de service et la gestion des groupes de ressources. Les rôles d'accès à un service définissent quant à eux les actions autorisées dans le cadre de l'utilisation d'un service. Ces rôles sont personnalisés en fonction du service sélectionné dans la règle.</dd>
<dt>Actions</dt>
<dd>Les actions sont mappées aux rôles Cloud IAM afin d'autoriser des utilisateurs à effectuer uniquement les tâches spécifiques associées aux différents rôles qui leur sont affectés. Les actions autorisées pour chaque rôle peuvent varier en fonction du service accédé car chaque service définit comment ce rôle est mappé à l'utilisation du service. </dd>
<dt>Système de gestion des accès</dt>
<dd>Le système de contrôle de Cloud IAM autorise ou refuse des actions d'utilisateur dans le contexte d'un service sur la base de la règle affectée. Lorsqu'un utilisateur tente d'effectuer une action spécifique, le système de contrôle utilise les attributs définis dans la règle pour déterminer si l'utilisateur est autorisé à effectuer cette tâche.</dd>
</dl>
