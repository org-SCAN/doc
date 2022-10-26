# Fields

## Get fields

This query retrieves the list of fields of the application.

This call provides all the lists registered on the server. The fields being considered as a list, they are part of the response sent by the server.

Here is the structure returned by the server:

```json
{
    "list_name" : {
        "first_list_elem_id" : {
            "displayed_element" : {
                "eng" : "English content",
                "fra" : "Contenu en français",
                …
            }
        },
        "second_list_elem_id" : {
            "displayed_element" : {
                "eng" : "English content",
                "fra" : "Contenu en français",
                …
            }
        }
    },
    "list_name2":{
        …
    },
    …
}
```

Please note that `displayed_value` holds the value of the list item in all languages supported by the application.\
It is also possible to have additional information for each list.

{% swagger method="get" path="/fields" baseUrl="https://app.netw4ppl.tech/api" summary="" %}
{% swagger-description %}
This query retrieves the list of fields of the application.
{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" required="true" %}
Bearer {Token API}
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Application-id" required="true" %}

{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}
```json
{
    "fields": {
        "1f1a01b1-3d1b-49a3-ab4e-c1c0887b6bc4": {
            "label": "unique_id",
            "placeholder": "AAA-000001",
            "database_type": "string",
            "android_type": "EditText",
            "linked_list": "",
            "required": 0,
            "best_descriptive_value": 0,
            "descriptive_value": 1,
            "displayed_value": {
                "eng": "Unique ID",
                "fra": "ID Unique",
                "spa": "Unico ID"
            }
        },
        "a97b52b4-a17c-46b9-b821-e41559b6883e": {
            "label": "gender",
            "placeholder": "F",
            "database_type": "string",
            "android_type": "Spinner",
            "linked_list": "e22bb1fa-7318-4161-b821-cb22bdf13dfa",
            "required": 1,
            "best_descriptive_value": 0,
            "descriptive_value": 1,
            "displayed_value": {
                "eng": "Sex",
                "fra": "Sexe",
                "spa": "Sexo"
            }
        },
        "94d39b16-8aca-4f4b-9bd0-41acb71b277e": {
            "label": "full_name",
            "placeholder": "John Doe",
            "database_type": "string",
            "android_type": "EditText",
            "linked_list": "",
            "required": 1,
            "best_descriptive_value": 1,
            "descriptive_value": 1,
            "displayed_value": {
                "eng": "Full Name",
                "fra": "Nom complet",
                "spa": "Nombre completo"
            }
        },
        "a78e429a-4d9d-42c2-bfee-0c4e080631d1": {
            "label": "age",
            "placeholder": "",
            "database_type": "integer",
            "android_type": "EditText",
            "linked_list": "",
            "required": 1,
            "best_descriptive_value": 0,
            "descriptive_value": 0,
            "displayed_value": {
                "eng": "Age (years)",
                "fra": "Age (années)",
                "spa": "Edad (años)"
            }
        },
        "22ce0190-1a35-4c61-ac8d-4c41c06145c5": {
            "label": "nationality",
            "placeholder": "Switzerland",
            "database_type": "string",
            "android_type": "AutoCompleteTextView",
            "linked_list": "0d2f93bb-96a6-4472-8a08-fa82070e9db4",
            "required": 2,
            "best_descriptive_value": 0,
            "descriptive_value": 1,
            "displayed_value": {
                "eng": "Nationality",
                "fra": "Nationalité",
                "spa": "Nacionalidad"
            }
        },
        "a32059b2-9166-4c06-8c4b-bffcd634cf25": {
            "label": "role",
            "placeholder": "",
            "database_type": "string",
            "android_type": "Spinner",
            "linked_list": "ccc69e4a-b583-488b-8a99-3e8142f012dc",
            "required": 2,
            "best_descriptive_value": 0,
            "descriptive_value": 1,
            "displayed_value": {
                "eng": "Role",
                "fra": "Role",
                "spa": "Papel"
            }
        },
        "ac0f8e3e-1d47-43ee-a1a6-3ce04b198c43": {
            "label": "birth_date",
            "placeholder": "YYYY-mm-dd",
            "database_type": "date",
            "android_type": "CalendarView",
            "linked_list": "",
            "required": 2,
            "best_descriptive_value": 0,
            "descriptive_value": 0,
            "displayed_value": {
                "eng": "Date of birth",
                "fra": "Date de naissance",
                "spa": "Fecha de nacimiento"
            }
        },
        "447cbb5a-7436-4f2f-9427-788b9e7ddbfe": {
            "label": "birth_place",
            "placeholder": "Paris",
            "database_type": "string",
            "android_type": "EditText",
            "linked_list": "",
            "required": 2,
            "best_descriptive_value": 0,
            "descriptive_value": 0,
            "displayed_value": {
                "eng": "Place of birth",
                "fra": "Lieu de naissance",
                "spa": "Lugar de nacimiento"
            }
        },
        "747592d3-7d24-499d-a4be-a4c289e6ed29": {
            "label": "passport_number",
            "placeholder": "",
            "database_type": "string",
            "android_type": "EditText",
            "linked_list": "",
            "required": 2,
            "best_descriptive_value": 0,
            "descriptive_value": 0,
            "displayed_value": {
                "eng": "Passport number",
                "fra": "Numéro de passeport",
                "spa": "Número de pasaporte"
            }
        },
        "b65a3348-8be4-45d6-af7f-56c938f26418": {
            "label": "destination",
            "placeholder": "",
            "database_type": "string",
            "android_type": "EditText",
            "linked_list": "",
            "required": 2,
            "best_descriptive_value": 0,
            "descriptive_value": 0,
            "displayed_value": {
                "eng": "Travel to",
                "fra": "Destination",
                "spa": "Viajar a"
            }
        },
        "97413115-4841-4893-beeb-3f08eb2f237a": {
            "label": "route",
            "placeholder": "",
            "database_type": "string",
            "android_type": "Spinner",
            "linked_list": "9ee12678-0ea3-44bb-aab1-b54e8f900d4c",
            "required": 2,
            "best_descriptive_value": 0,
            "descriptive_value": 0,
            "displayed_value": {
                "eng": "Route",
                "fra": "Route",
                "spa": "Camino"
            }
        },
        "6573f876-10d8-4a2e-91dd-b67665bde8c8": {
            "label": "residence",
            "placeholder": "Syria",
            "database_type": "string",
            "android_type": "AutoCompleteTextView",
            "linked_list": "0d2f93bb-96a6-4472-8a08-fa82070e9db4",
            "required": 2,
            "best_descriptive_value": 0,
            "descriptive_value": 0,
            "displayed_value": {
                "eng": "Country of residence",
                "fra": "Pays de residence",
                "spa": "País de residencia"
            }
        },
        "446290ca-d42f-475e-a924-001283b3fba8": {
            "label": "alias",
            "placeholder": "Big Joe",
            "database_type": "string",
            "android_type": "EditText",
            "linked_list": "",
            "required": 3,
            "best_descriptive_value": 0,
            "descriptive_value": 0,
            "displayed_value": {
                "eng": "Alias",
                "fra": "Alias",
                "spa": "Alias"
            }
        },
        "3f47cfb3-32e7-4326-af1b-4ffd2da1a22c": {
            "label": "embarkation_date",
            "placeholder": "YYYY-mm-dd",
            "database_type": "date",
            "android_type": "CalendarView",
            "linked_list": "",
            "required": 3,
            "best_descriptive_value": 0,
            "descriptive_value": 0,
            "displayed_value": {
                "eng": "Embarkation date",
                "fra": "Date d'embarcation",
                "spa": "Fecha de embarque"
            }
        },
        "26a8ed39-0f61-414a-be66-51d51730703e": {
            "label": "embarkation_place",
            "placeholder": "Roubaix",
            "database_type": "string",
            "android_type": "EditText",
            "linked_list": "",
            "required": 3,
            "best_descriptive_value": 0,
            "descriptive_value": 0,
            "displayed_value": {
                "eng": "Place of embarkation",
                "fra": "Lieu d'embarcation",
                "spa": "Lugar de embarque"
            }
        },
        "e156f7b6-2c9f-4773-a51a-a74834f2f815": {
            "label": "detention_place",
            "placeholder": "Aleppo",
            "database_type": "string",
            "android_type": "EditText",
            "linked_list": "",
            "required": 3,
            "best_descriptive_value": 0,
            "descriptive_value": 0,
            "displayed_value": {
                "eng": "Place of Detention",
                "fra": "Lieu de détention",
                "spa": "Lugar de detención"
            }
        },
        "ab4ee8fa-83e9-4156-b52c-dc641475aece": {
            "label": "date_last_seen",
            "placeholder": "YYYY-mm-dd",
            "database_type": "date",
            "android_type": "CalendarView",
            "linked_list": "",
            "required": 3,
            "best_descriptive_value": 0,
            "descriptive_value": 0,
            "displayed_value": {
                "eng": "Date when last seen well",
                "fra": "Date de la dernière fois vu en forme",
                "spa": "Fecha de la última vez que fue bueno"
            }
        },
        "ba332a63-cf7d-437d-adb5-82931ce5a690": {
            "label": "mothers_names",
            "placeholder": "",
            "database_type": "string",
            "android_type": "EditText",
            "linked_list": "",
            "required": 3,
            "best_descriptive_value": 0,
            "descriptive_value": 0,
            "displayed_value": {
                "eng": "Mother's full names",
                "fra": "Nom de la mère",
                "spa": "Nombres completos de la madre"
            }
        },
        "75947d07-05a7-4ee0-897d-64895131cc98": {
            "label": "fathers_names",
            "placeholder": "",
            "database_type": "string",
            "android_type": "EditText",
            "linked_list": "",
            "required": 3,
            "best_descriptive_value": 0,
            "descriptive_value": 0,
            "displayed_value": {
                "eng": "Father's full names",
                "fra": "Nom du père",
                "spa": "Nombres completos del padre"
            }
        },
        "4ae6fa88-181c-4ff8-b8af-47921a972daa": {
            "label": "detail",
            "placeholder": "Phone number",
            "database_type": "text",
            "android_type": "EditText",
            "linked_list": "",
            "required": 4,
            "best_descriptive_value": 0,
            "descriptive_value": 0,
            "displayed_value": {
                "eng": "Details",
                "fra": "Informations supplémentaires",
                "spa": "Informaciones suplementarias"
            }
        }
    },
    "ListRelations": {
        "65a5e627-23e1-4fe2-884a-e162f7112988": {
            "color": "734d39",
            "importance": 1,
            "short": "SA",
            "displayed_value": {
                "eng": "Saw",
                "fra": "A vu",
                "spa": "Ha visto"
            }
        },
        "9c4e9438-1f2d-4b2d-8d5d-8bea347d5d95": {
            "color": "00ff2a",
            "importance": 1,
            "short": "TW",
            "displayed_value": {
                "eng": "Travelled with",
                "fra": "A voyagé avec",
                "spa": "Viajado con"
            }
        },
        "9d7e86ac-5de8-4e4e-bbdb-c0d2bc5efe3d": {
            "color": "7e00ff",
            "importance": 1,
            "short": "SE",
            "displayed_value": {
                "eng": "Service",
                "fra": "Service",
                "spa": "Servicio"
            }
        },
        "a98467e8-8ae4-4105-b0e4-ad8691ffb852": {
            "color": "cbaf1d",
            "importance": 1,
            "short": "NBR",
            "displayed_value": {
                "eng": "Non-biological relationship",
                "fra": "Relation non biologique",
                "spa": "Relación no biológica"
            }
        },
        "dd082289-d708-4d9b-93dd-2eee9fc0df07": {
            "color": "0099ff",
            "importance": 1,
            "short": "BR",
            "displayed_value": {
                "eng": "Biological relationship",
                "fra": "Relation biologique",
                "spa": "Relación biológica"
            }
        }
    }
}
```
{% endswagger-response %}

{% swagger-response status="500: Internal Server Error" description="Can be returned if Application-Id is missing" %}
```json
{
    "message": "Server Error"
}
```
{% endswagger-response %}
{% endswagger %}
