---
description: Optionnal section
---

# Implicitly Linked Permissions

(Just skip this page and go to [inviting-members.md](../inviting-members.md "mention") if you are not interested in permissions for now).

Here is a table representing a proposal of the implicitly linked permissions :&#x20;

| Permission | Implicitly Linked Permission    |
| ---------- | ------------------------------- |
| .show      | .index                          |
| .store     | .show, .index, .edit, .destroy  |
| .edit      | .show, .index, .store, .destroy |
| .destroy   | show, .index, .store, .edit     |
