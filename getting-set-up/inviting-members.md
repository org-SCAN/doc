---
description: Introduction to Teams
---

# 🫂 Teams

A team allows to gather different users around the same data set. Each team is independent from each other which allows SCAN to have different forms and to collect data in multiple contexts.

## Creating a new team

To create a new team :

1. Click on Teams (User Management section)
2. Click on Add a team
3. Fill the name and create
4. You're done !

<figure><img src="../.gitbook/assets/create_team.gif" alt=""><figcaption><p>How to create a team in 10 seconds ?</p></figcaption></figure>

## Add user to a team

Once your team is created, you can add user to this team.

A user only sees the information of the team he is in. In other words, by changing the team of a user, he will no longer see the dataset of the team he belonged to before. You can always reassign the user to his old team so that he regains access to the old data. Note that some users with the user.changeTeam permission can change their team themselves by following this procedure: [change-my-team.md](../basic-usage/my-profile/change-my-team.md "mention").

{% hint style="warning" %}
You must have the required permissions to perform this operation
{% endhint %}

{% hint style="danger" %}
**Warning :** This will remove the user from his current team
{% endhint %}

You just have to :

1. Click on the name of the team you want to add the user to
2. In the 'User in team section', select the user you want to add to the team and add him

<figure><img src="../.gitbook/assets/add_user_to_team.gif" alt=""><figcaption><p>Add a user to a team</p></figcaption></figure>

{% hint style="info" %}
Please note that it is also possible to change the team of a user directly from his edition page (in User Management).
{% endhint %}

If we refer to our infrastructure graph, the change of a user's team can be represented as follows:

<figure><img src="../.gitbook/assets/image (1) (3).png" alt=""><figcaption><p>User 3 switching from Team 2 to Team 1 (=> he will now see all the persons created in Team 1)</p></figcaption></figure>

## Remove a user from a team

A user **must necessarily belong to a team**. It is therefore not possible to remove him from a team. If you don't want a user to have access to your team anymore, you have to put him in another team. To do this, simply [follow the procedure described above.](inviting-members.md#add-user-to-a-team)

## Update or Delete a team

To update or delete a team, you should :

1. Click on the name of the team you want to edit/delete
2. Clic on edit or delete

{% hint style="warning" %}
When you delete a team, all its users are automatically assigned to the default team, and all associated data are deleted.
{% endhint %}
