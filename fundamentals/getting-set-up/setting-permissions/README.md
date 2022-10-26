# 👨🔧 Users & Roles

In this section you will learn how to create new users.&#x20;

These users will have a particular login, a **team** and a **role**.&#x20;

### Default and Specific Roles

The role defines the permissions associated with the user. There are three default roles in SCAN:

| Default roles                  | Permissions                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| ------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <pre><code>admin</code></pre>  | <pre><code>*   // all permissions</code></pre>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| <pre><code>editor</code></pre> | <p></p><pre><code>cytoscape.index 
person.create_from_json 
links.create_from_json 
person.store_from_json 
links.store_from_json 
user.request_role 
lists_control.add_to_list 
person.fix_duplicated_reference 
person.index person.create 
person.store person.show 
person.edit person.update 
person.destroy 
links.index
links.create 
links.store 
links.show 
links.edit 
links.update 
links.destroy 
user.change_team 
user.request_role 
duplicate.index 
duplicate.create 
duplicate.store 
duplicate.show 
duplicate.edit 
duplicate.update 
duplicate.destroy</code></pre> |
| <pre><code>viewer</code></pre> | <p></p><pre><code>cytoscape.index
person.index
person.show
links.index
links.show</code></pre>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |

Each time you create a user, you assign him a role, which gives him the associated permissions.&#x20;

\=> In most cases, these three roles are sufficient.&#x20;

If you want a **higher granularity**, here is how to create **new roles** (If not, you can go straight to the [#creating-a-new-user](./#creating-a-new-user "mention") step) :&#x20;

### Creating a new Role

To do this, go to the "Role" page in the "User Management" section :

<figure><img src="../../../.gitbook/assets/image (3).png" alt=""><figcaption><p>Role index page (there are already the3 default roles)</p></figcaption></figure>

By clicking on "New Role", you will be able to access the role creation page (i.e. associated to "role.create" permission) :&#x20;

<figure><img src="../../../.gitbook/assets/image (6).png" alt=""><figcaption><p>role creation page</p></figcaption></figure>

On this page, you can associate a name to your new role, then check one by one all the permissions you want your role to have.&#x20;

To help you, you also have "all" checkboxes, which allow you to check all the checkboxes of a category directly.

{% hint style="info" %}
Beware, some permissions are implicitly linked, and if you don't check both, bugs may occur.&#x20;

For example, if you check _person.show_ but not _person.index_, your role will be able to inspect a particular person but will not be able to access the index page of all persons.

You can see a table of these linked permissions here : [#implicitly-linked-permissions](all-permissions.md#implicitly-linked-permissions "mention")
{% endhint %}

To save your role, just click on the **Create** button.

<figure><img src="../../../.gitbook/assets/image (7).png" alt=""><figcaption><p>Create button (Use it to save your new role)</p></figcaption></figure>

You can now see your new role in the list of existing roles. You can modify it by clicking on _Edit_, and even delete it with the _Delete_ button.

<figure><img src="../../../.gitbook/assets/image (5).png" alt=""><figcaption><p>New index of roles</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (4).png" alt=""><figcaption><p>show view of the New role (note the delete button)</p></figcaption></figure>

We can now proceed to the creation of new users.

### Creating a new User <a href="#creating-a-new-user" id="creating-a-new-user"></a>

You can now go to the _Users_ section in _User management_. You will see the index of the different existing roles.

<figure><img src="../../../.gitbook/assets/image.png" alt=""><figcaption><p>User index</p></figcaption></figure>

By clicking on _Add user_, you will arrive on this page of User creation :&#x20;

<figure><img src="../../../.gitbook/assets/image (8).png" alt=""><figcaption><p>User creation</p></figcaption></figure>

You will then have several fields to fill in:&#x20;

* The **name** of the user,&#x20;
* his **logins** (email and password),&#x20;
* his **role** (among those by default or one of the new ones you can create)&#x20;
* and finally his **team** (<mark style="color:orange;">by default DEFAULT\_ICRC</mark>).

You then register your user by clicking on the Create button at the end of the page, and you can then send his logins to your colleague.&#x20;

Like any field in our application, you can edit your user at any time (to change his role for example), but also delete him.

Let's now look at the **Teams** notion, mentioned earlier.
