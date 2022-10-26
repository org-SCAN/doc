# ⚙ Roles

### Default and Specific Roles

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
person.createFromJson
links.createFromJson
person.createFromJson
links.createFromJson
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
duplicate.index 
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

Each time you create a user, you assign him a role, which gives him the associated permissions.&#x20;

{% hint style="success" %}
&#x20;In most cases, these three roles are sufficient.&#x20;
{% endhint %}

If you want a **higher granularity**, here is how to create **new Roles** (if not, you go skip this part and go to [inviting-members.md](../inviting-members.md "mention")) **:**

### Permissions

A permission is defined according to the following format:

$$
Notion.Action
$$

For instance, here is a common permission from our solution :

```
person.viewAny
```

The first part refers to the notion, here **Person**.&#x20;

The second part refers to the desired action: here **viewAny (= index)**

{% hint style="success" %}
If your User has a Role that count "person.index" in its permissions, then your user is able to index (view Any) the persons = acces the page _/person_
{% endhint %}

### Creating a new Role

{% hint style="warning" %}
Please note that to access this page, you need the necessary permissions
{% endhint %}

To create a new role, go to the "Role" page in the "User Management" section :

<figure><img src="../../../.gitbook/assets/image (3).png" alt=""><figcaption><p>Role index page (there are already the3 default roles)</p></figcaption></figure>

By clicking on "New Role", you will be able to access the role creation page (i.e. associated to "role.create" permission) :&#x20;

<figure><img src="../../../.gitbook/assets/image (6).png" alt=""><figcaption><p>role creation page</p></figcaption></figure>

On this page, you can associate a name to your new role, then check one by one all the permissions you want your role to have.&#x20;

To help you, you also have "all" checkboxes, which allow you to check all the checkboxes of a category directly.

{% hint style="info" %}
Beware, some permissions are implicitly linked, and if you don't check both, bugs may occur.&#x20;

For example, if you check _person.show_ but not _person.index_, your role will be able to inspect a particular person but will not be able to access the index page of all persons.

You can see a table of these linked permissions here : [#implicitly-linked-permissions](implicitly-linked-permissions.md#implicitly-linked-permissions "mention")
{% endhint %}

To save your role, just click on the **Create** button.

<figure><img src="../../../.gitbook/assets/image (7).png" alt=""><figcaption><p>Create button (Use it to save your new role)</p></figcaption></figure>

You can now see your new role in the list of existing roles. You can modify it by clicking on _Edit_, and even delete it with the _Delete_ button.

<figure><img src="../../../.gitbook/assets/image (5).png" alt=""><figcaption><p>New index of roles</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (4).png" alt=""><figcaption><p>show view of the New role (note the delete button)</p></figcaption></figure>

The next page is about the implicitly linked permissions, if you are not interested you can go straight to [inviting-members.md](../inviting-members.md "mention").
