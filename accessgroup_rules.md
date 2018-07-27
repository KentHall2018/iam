---

copyright:

  years: 2018

lastupdated: "2018-07-11"

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:tip: .tip}

# Creating dynamic rules for access groups
{: #rules}

You can create dynamic rules to automatically add federated users to access groups based on specific identity attributes. When your users log in with a federated ID, the data from the identity provider dynamically maps your users to an access group based on the rules that you set.

Users already have specific identity information within your company's domain, and when they log in with a federated ID, this data can be passed through by using SAML assertions. The SAML assertions or attribute statements that are configured within the identity provider provide the data that is used to create each rule. For example, there might be a true or false attribute statement that defines users as a manager. This information can be used to add all users who are managers to a specific access group for managers that you created in your {{site.data.keyword.Bluemix_notm}} account. For more information, see the [Example rule](accessgroup_rules.html#example).

Only users who are already invited to the account can be mapped to access groups by using dynamic rules.
{: tip}

## Setting up rules

Dynamic rules are created by setting conditions that must be matched by the data that is configured within the identity provider and passed in with a user's federated ID during login. To create a rule, follow these steps:

1. From the menu bar, click **Manage** &gt; **Security** &gt; **Identity and access**, and then select **Access Groups**.
2. Select the name of the access group that you want to create a rule for to open the group details page.
3. Select the **Dynamic rules** tab.
4. Click **Add rule**.
5. Enter the information from your identity provider. The following list provides details for each required field.

<dl>
<dt>Name</dt>
<dd>Enter a custom name for your rule that helps you remember what type of users you are adding to an access group.</dd>
<dt>Identity provider</dt>
<dd>Enter the URI for your identity provider. This is the SAML "entityId" field, which is sometimes referred to as the issuer ID, for the identity provider as part of the federation configuration for onboarding with IBMid.</dd>
<dt>Expiration (in hours)</dt>
<dd>You can use this option to provide extra security by setting a time limit for the assigned access. Each user must log in every 24 hours to refresh their access, but you can set the access to expire in as little as an hour's time. Group membership is revoked after this time period expires.</dd>
<dt>Add users when</dt>
<dd>The attribute statement name must be entered in this field. This value is specific to your identity provider.</dd>
<dt>Comparator</dt>
<dd>You can choose from Equals, Not Equals, Equals Ignore Case, Not Equals Ignore Case, In, and Contains. Use the Contains option when the attribute statement has an array type. And, you can enter more than one value to be matched by using the In option.</dd>
<dt>Value</dt>
<dd>Enter the attribute value for the attribute statement that the rule is comparing against.</dd>
</dl>

You can add more than one condition for a rule. All conditions set in the rule must be met for a user to be added to an access group.
{: tip}

## Example rule
{: #example}

The following example includes values for each of the fields on the **Add rule** page. In this rule, users who are identified as managers within the federated identity provider are mapped to an {{site.data.keyword.Bluemix_notm}} access group that has specific access set for only managers.

| Field | Value |
|----------|---------|
| Name | Manager group rule |
| Identity provider | `https://idp.example.org/SAML2` |
| Expiration (in hours) | 12 |
| Add users when (attribute name) | isManager |
| Comparator | Equals  |
| Value |  true |
{: caption="Table 1. Example dynamic rule for access groups" caption-side="top"}
