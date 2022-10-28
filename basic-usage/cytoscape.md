# 📊 Cytoscape

The graph of our network is created with the cytoscape library.

It is accessible via the "Network graph" tab. It is automatically created as soon as you have at least 1 person in your team database.

{% hint style="success" %}
You will see on this graph only the persons registered in your team.
{% endhint %}

<figure><img src="../.gitbook/assets/image (2) (1).png" alt=""><figcaption><p>Network graph of our fake situation from the last section (for the rest of this documentation we will work with another situation)</p></figcaption></figure>

On this graph, you can see the people (colored according to their role if they have one), as well as the relations, with a color code specified in the chart.

{% hint style="danger" %}
The colors are not dynamic at the moment, so if I add a new role in the list, it will not have a color automatically associated with it
{% endhint %}

### Filtering and features

The library allows us to have a large number of filters and features on our graph to better navigate and inspect our elements.

Here is a non-exhaustive list of what you can do :&#x20;

1. &#x20;You can filter the relationships and display only those of a particular person. You can also search by specifying the "starting" person of the relationship and the "ending" person.

<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption><p>Result of the filtering by "Pinkie Gislason Sr."</p></figcaption></figure>



&#x20; 2\.  We have a contextual "wheel" menu that can be accessed by holding down the right mouse button and dragging the mouse to the chosen option :&#x20;

<figure><img src="../.gitbook/assets/image (4).png" alt=""><figcaption><p>Contextual wheel</p></figcaption></figure>

This wheel has several options that you can select :&#x20;

* Degre, Cise, Fcose and Breathfirst layout : these are automatic layouts that allow you to place all the nodes according to a precise organization.
* Show and Hide realtions details : These options allow you to show or hide the details of the relationships. This information is optional when creating the relationship.

Here is an example of the different features of this wheel : <mark style="color:purple;">(insert gif)</mark>

<mark style="color:purple;"></mark>

&#x20; 3\.  You can also move the nodes with drag and drop and right click on them to display another <mark style="color:purple;"></mark> wheel menu. The menu is specific to the node on which the menu was called.

<figure><img src="../.gitbook/assets/image (2).png" alt=""><figcaption><p>Node specific whell menu</p></figcaption></figure>

This node wheel has several options that you can select :&#x20;

* Set as FROM/TO : This function is equivalent to sorting the relations at the departure or arrival of this person (in the same way as in part 1.)
* View information : This redirects to the details (show) page of the selected person
* View related persons : This makes it possible to hide all persons who do not have a direct or indirect relationship with the selected person
* Save position : This allows you to save the position of a particular node for the user's profile <mark style="color:yellow;">(NOT CURRENTLY FUNCTIONING)</mark>

Here is an example of the different features of this wheel : <mark style="color:purple;">(insert gif)</mark>

<mark style="color:purple;"></mark>

&#x20; <mark style="color:purple;"></mark>  4. Finally, you can also calculate the betweenness centrality of a person with the corresponding button. The more central a person is in the overall architecture, the more its node will be colored towards red.

<figure><img src="../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

