# 📋 Lists

The list is a type of field pre-filled with several values.

By default there are already pre-filled lists, like the list of all countries or the most used migration routes.

<figure><img src="../.gitbook/assets/image (3) (2) (1).png" alt=""><figcaption><p>Default pre-filled lists</p></figcaption></figure>

Here is a look at the list of countries :

<figure><img src="../.gitbook/assets/image (13).png" alt=""><figcaption><p>List of countries</p></figcaption></figure>

### Use a list as a field

For example, we would like to create a field for our form where the user would have to fill in the initial destination country of a person.

<figure><img src="../.gitbook/assets/image (3) (3).png" alt=""><figcaption><p>Bottom of the F<strong>ield creation page</strong> : we choose the country list</p></figcaption></figure>

If we create a field called "Destination" and attach the list countries to it (as seen in the image above), then the user will have a dropdown in his creation form containing all the countries and will be able to select one for the value of this field :

<figure><img src="../.gitbook/assets/image (14) (1).png" alt=""><figcaption><p>Bottom of the <strong>Person creation page</strong> : the user have to choose a country from the list as a destination.</p></figcaption></figure>

### Create a new List

If you have a particular need you can create new lists that you can populate manually. For example, you could create the list "birds" which contains the 20 most common bird species ( => "Add list" button on the List index page).

You wil have 3 fields to fill during the creation process :

* **List's title** : This is simply the name given to your list
* **List's fields** : In this section, you may define all the fields that are required to describe an element of your list. As an example you can create 'name', 'color' if you want to create a list related to Birds.
* **Displayed value** : here you have to choose one of the fields of the elements of your list as displayed value : if you choose the 'name' field, the name of the element will be shown in the dropdown when choosing one of the birds.

You will then have the following view: your list is empty, you just have to populate it with the "Add an element to the list" button.

<figure><img src="../.gitbook/assets/image (15) (1).png" alt=""><figcaption><p>empty list of common birds</p></figcaption></figure>

When adding a new element to the list, you will need to fill all the required fields :

<figure><img src="../.gitbook/assets/image (16).png" alt=""><figcaption><p>add to common birds view</p></figcaption></figure>

You will then have your list, populated with the elements you want :

<figure><img src="../.gitbook/assets/image (18) (1).png" alt=""><figcaption><p>common bird populated list</p></figcaption></figure>

Now, if you want to use our solution to reference the birds you saw in your garden, you just have to create a new team, and create one field as an extension of the common birds list :

<figure><img src="../.gitbook/assets/image (5) (2).png" alt=""><figcaption><p>Using common birds list as the associated list when creating the field</p></figcaption></figure>

So, when a user of your team adds an item it will look like this :

<figure><img src="../.gitbook/assets/image (17).png" alt=""><figcaption><p>adding a 'person' inside the new team "birds_lover" with asingle field bird (with associated list "common bird")</p></figcaption></figure>

You now know all the details of SCAN's modularity, and your form is ready to be used by all the users in your team.

{% hint style="success" %}
In the next section, we will detail the classic use of SCAN on the editor/viewer side.
{% endhint %}
