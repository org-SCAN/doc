# ⚙ Roles

## Default and Specific Roles

The role defines the permissions associated with the user. There are three default roles in SCAN:

<details>

<summary>Admin</summary>

Permissions :

```
*   // all permissions
```

</details>

<details>

<summary>Editor</summary>

Permissions :

```
cytoscape.viewAny 
links.createFromJson
person.createFromJson
user.requestRole
lists_control.addToList
person.fixDuplicatedReference
person.viewAny
person.create
person.view
person.update 
person.delete
links.viewAny
links.create 
links.view 
links.update 
links.delete
user.changeTeam
user.requestRole
duplicate.viewAny
duplicate.create 
duplicate.view
duplicate.update 
duplicate.delete
```

</details>

<details>

<summary>Viewer</summary>

Permissions :

```
cytoscape.viewAny
person.viewAny
person.view
links.viewAny
links.view
```

</details>

Each time you create a user, you assign him a role, which gives him the associated permissions.

{% hint style="success" %}
In most cases, these three roles are sufficient.
{% endhint %}

If you want a **higher granularity**, here is how to create **new Roles** (if not, you go skip this part and go to [inviting-members.md](../inviting-members.md "mention")) **:**

## Permissions

A permission is defined according to the following format:

$$
Notion.Action
$$

For instance, here is a common permission from our solution :

```
person.viewAny
```

The first part refers to the notion, here **Person**.

The second part refers to the desired action: here **viewAny (= index)**

{% hint style="success" %}
If your User has a Role that count "person.index" in its permissions, then your user is able to index (view Any) the persons = acces the page _/person_
{% endhint %}

Here are the permissions given by the main action :

| Action  | Description                                                                                                                   |
| ------- | ----------------------------------------------------------------------------------------------------------------------------- |
| viewAny | <p>Allow the user to index (view Any) all ressources of a given notion.<br><em>E.g: the table showing all the people</em></p> |
| view    | <p>Allow the user to view the detail of a given notion.<br><em>E.g : view the detail of one person</em></p>                   |
| create  | <p>Allow the user to create a new entity of a given notion.<br>E.g : create a new person</p>                                  |
| update  | <p>Allow the user to edit an entity of a given notion.<br>E.g : edit a person</p>                                             |
| delete  | <p>Allow the user to delete an entity of a given notion.<br>E.g : delete a person</p>                                         |

{% hint style="info" %}
More specific action exists. They are detailled in the [#actions-permissions](implicitly-linked-permissions.md#actions-permissions "mention") section
{% endhint %}

## Creating a new Role

{% hint style="warning" %}
Please note that to access this page, you need the necessary permissions
{% endhint %}

To create a new role, go to the "Role" page in the "User Management" section :

<figure><img src="../../../.gitbook/assets/image (3).png" alt=""><figcaption><p>Role index page (there are already the3 default roles)</p></figcaption></figure>

By clicking on "New Role", you will be able to access the role creation page (i.e. associated to "role.create" permission) :

<figure><img src="../../../.gitbook/assets/image (6).png" alt=""><figcaption><p>role creation page</p></figcaption></figure>

On this page, you must associate a name to your new role, then check one by one all the permissions you want your role to have.

To help you, you also have "all" checkboxes, which allow you to check all the checkboxes of a category directly.

{% hint style="info" %}
Beware, some permissions are implicitly linked, and if you don't check both, bugs may occur.

For example, if you check _person.show_ but not _person.index_, your role will be able to inspect a particular person but will not be able to access the index page of all persons.

You can see a table of these linked permissions here :[#implicitly-linked-actions](implicitly-linked-permissions.md#implicitly-linked-actions "mention")
{% endhint %}

To save your role, just click on the **Create** button.

{% hint style="warning" %}
Did you remember to put a name ?
{% endhint %}

<figure><img src="../../../.gitbook/assets/image (7) (1).png" alt=""><figcaption><p>Create button (Use it to save your new role)</p></figcaption></figure>

You can now see your new role in the list of existing roles. You can modify it by clicking on _Edit_, and even delete it with the _Delete_ button.

<figure><img src="../../../.gitbook/assets/image (5).png" alt=""><figcaption><p>New index of roles</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (4) (1).png" alt=""><figcaption><p>show view of the New role (note the delete button)</p></figcaption></figure>

The next page is about the implicitly linked permissions, if you are not interested you can go straight to [inviting-members.md](../inviting-members.md "mention").
