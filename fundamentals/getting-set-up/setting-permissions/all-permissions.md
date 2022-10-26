---
description: Optionnal section
---

# All permissions

Here is a complete list of the permissions you can assign to a given user. (Just skip this page and go to [inviting-members.md](../inviting-members.md "mention") if you are not interested in permissions for now).

Each permission is identified by its controller name, and each controller name has an equivalent policy name.&#x20;

(This is just useful for the developer, but also helps you understand if a bug ever occurs.)

| CONTROLLER NAME                   | POLICY NAME                   |
| --------------------------------- | ----------------------------- |
| api\_logs.create                  | api\_logs.create              |
| api\_logs.destroy                 | api\_logs.delete              |
| api\_logs.update                  | api\_logs.update              |
| api\_logs.show                    | api\_logs.view                |
| api\_logs.index                   | api\_logs.viewAny             |
| crew.addUser                      | crew.addUser                  |
| crew.store                        | crew.create                   |
| crew.destroy                      | crew.delete                   |
| crew.edit                         | crew.update                   |
| crew.show                         | crew.view                     |
| crew.index                        | crew.viewAny                  |
| cytoscape.index                   | cytoscape.viewAny             |
| duplicate.create                  | duplicate.create              |
| duplicate.destroy                 | duplicate.delete              |
| duplicate.update                  | duplicate.update              |
| duplicate.show                    | duplicate.view                |
| duplicate.index                   | duplicate.viewAny             |
| fields.store                      | fields.create                 |
| fields.destroy                    | fields.delete                 |
| fields.edit                       | fields.update                 |
| fields.show                       | fields.view                   |
| fields.index                      | fields.viewAny                |
| links.store                       | links.create                  |
| links.store\_from\_json           | links.createFromJson          |
| links.destroy                     | links.delete                  |
| links.update                      | links.update                  |
| links.show                        | links.view                    |
| links.index                       | links.viewAny                 |
| lists\_control.add\_to\_list      | lists\_control.addToList      |
| lists\_control.create             | lists\_control.create         |
| lists\_control.destroy            | lists\_control.delete         |
| lists\_control.delete\_list\_elem | lists\_control.deleteListElem |
| lists\_control.update             | lists\_control.update         |
| lists\_control.update\_list\_elem | lists\_control.updateListElem |
| lists\_control.show               | lists\_control.view           |
| lists\_control.index              | lists\_control.viewAny        |
| permissions.store                 | permissions.create            |
| permissions.destroy               | permissions.delete            |
| permissions.edit                  | permissions.update            |
| permissions.show                  | permissions.view              |
| permissions.index                 | permissions.viewAny           |
| person.create                     | person.create                 |
| person.store\_from\_json          | person.createFromJson         |
| person.destroy                    | person.delete                 |
| person.fix\_duplicated\_reference | person.fixDuplicatedReference |
| person.edit                       | person.update                 |
| person.show                       | person.view                   |
| person.index                      | person.viewAny                |
| roles.create                      | roles.create                  |
| roles.destroy                     | roles.delete                  |
| roles.edit                        | roles.update                  |
| roles.show                        | roles.view                    |
| roles.index                       | roles.viewAny                 |
| user.change\_team                 | user.changeTeam               |
| user.store                        | user.create                   |
| user.destroy                      | user.delete                   |
| user.grant\_role                  | user.grantRole                |
| user.request\_role                | user.requestRole              |
| user.edit                         | user.update                   |
| user.show                         | user.view                     |
| user.index                        | user.viewAny                  |

### Implicitly Linked Permissions <a href="#implicitly-linked-permissions" id="implicitly-linked-permissions"></a>

Here is a table representing a proposal of the implicitly linked permissions :&#x20;

| Permission | Implicitly Linked Permission    |
| ---------- | ------------------------------- |
| .show      | .index                          |
| .store     | .show, .index, .edit, .destroy  |
| .edit      | .show, .index, .store, .destroy |
| .destroy   | show, .index, .store, .edit     |
