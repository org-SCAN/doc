# 🗣 Persons

In the tab "persons" you have a table view of the entire database of your team.&#x20;

If you don't see anything, it's normal: nobody has added persons via your team form yet.&#x20;

\=> Let's see how to create our first entry.

### Add a person

<figure><img src="../.gitbook/assets/image (12).png" alt=""><figcaption><p>Add person page, with 4 fields.</p></figcaption></figure>

In this example, our team administrator has edited the form so that a person is characterized by three fields:

* Name: requires a text
* Age: requires a number
* Nationality : linked to the list of countries, it is a choice to be made in a dropdown.
* Sex : linked to a list of genders, it is a choice to be made in a dropdown.

### Browse the persons

After filling in the form several times with the desired data, we can arrive at this kind of view on the "Persons" tab :&#x20;

<figure><img src="../.gitbook/assets/image (6) (2).png" alt=""><figcaption><p>Index of the persons that your team has pushed to the database.</p></figcaption></figure>

In this table, it is possible to filter the elements by fields, in an increasing or decreasing way. It is also possible to make a general search via the "Search:" tool.

But you can only see on this display the fields Name, Age and Nationality. Indeed, the gender field was not created as a descriptive\_value, that's why it is not displayed on this page.

To see all the fields of a person, you have to click on its best\_descriptive_\__value, in our case its name:&#x20;

<figure><img src="../.gitbook/assets/image (8).png" alt=""><figcaption><p>view page of a person</p></figcaption></figure>

From this page, it is possible to modify the value of the person's fields by clicking on edit, but also to delete the person completely.



At the very end of a person's show page, you may have noticed a relationship section. This is perfect because it is the next step in this documentation.
