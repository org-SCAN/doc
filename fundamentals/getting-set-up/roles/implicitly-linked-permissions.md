---
description: Optionnal section
---

# Permissions

(Just skip this page and go to [inviting-members.md](../inviting-members.md "mention") if you are not interested in permissions for now).

## Implicitly linked actions

Here is a table representing a proposal of the implicitly linked permissions :

| Permission | Implicitly Linked Permission |
| ---------- | ---------------------------- |
| .view      | .viewAny                     |
| .create    | .viewAny                     |
| .update    | .view, .viewAny              |
| .delete    | .view, .viewAny              |

## Actions permissions

### Basic Action

| Action  | Description                                                                                                                   |
| ------- | ----------------------------------------------------------------------------------------------------------------------------- |
| viewAny | <p>Allow the user to index (view Any) all ressources of a given notion.<br><em>E.g: the table showing all the people</em></p> |
| view    | <p>Allow the user to view the detail of a given notion.<br><em>E.g : view the detail of one person</em></p>                   |
| create  | <p>Allow the user to create a new entity of a given notion.<br>E.g : create a new person</p>                                  |
| update  | <p>Allow the user to edit an entity of a given notion.<br>E.g : edit a person</p>                                             |
| delete  | <p>Allow the user to delete an entity of a given notion.<br>E.g : delete a person</p>                                         |

### Specific permissions

| Action                       | Description                                                              |
| ---------------------------- | ------------------------------------------------------------------------ |
| crew.addUser                 | Allow the user to add user to a given crew                               |
| links.createFromJson         | Allow the user to add relations from a json file                         |
| person.createFromJson        | Allow the user to add persons from a json file                           |
| list\_control.addToList      | Allow the user to add an element to a given list.                        |
| list\_control.deleteListElem | Allow the user to delete an element from a given list.                   |
| list\_control.updateListElem | Allow the user to edit an element from a given list.                     |
| user.requestRole             | Allow the user to request a new role. (This request should be accepted). |
| user.grantRole               | Allow the user to accept or decline requests for roles from other users. |
| user.changeTeam              | Allow the user to change teams.                                          |
