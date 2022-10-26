# Person

## Add

This query allows the addition of refugees. The body must be in **json format** and follow the following structure:

{% hint style="info" %}
Please note the `date` field
{% endhint %}

```json
[
    {
        'field_id_1': 'value 1-1',
        'field_id_2': 'value 2-1',
        'date': '',
        ...
    },
    {
        'field_id_1': 'value 1-2',
        'field_id_2': 'value 2-3',
        'date': ''
        ...
    }
]
```

{% hint style="warning" %}
The server may responds with an error if one of the required fields is not provided or if the data type is wrong.
{% endhint %}

{% hint style="success" %}
The server responds by listing the ids of the persons created
{% endhint %}

{% swagger method="post" path="/person" baseUrl="https://netw4ppl.tech/api" summary="Add persons" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" required="true" %}
Bearer <API TOKEN>
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Application-id" required="true" %}
\<Application-id>
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Content-Type" %}
application/json
{% endswagger-parameter %}

{% swagger-parameter in="body" name="body" type="json" %}
See 

[#add](person.md#add "mention")


{% endswagger-parameter %}

{% swagger-response status="201: Created" description="" %}
```json
[
    "a9314fb6-8614-474e-9b89-b26ac27a2703",
    "7d8fd444-bd35-4d7a-93ba-f88e7e735a3c",
    "59cf9cdb-634b-4f79-a0da-e618c9b5f163"
]
```
{% endswagger-response %}

{% swagger-response status="422: Unprocessable Entity" description="Returns the list of invalid fields" %}
```json
{
    "message": "The given data was invalid.",
    "errors": {
        "0.full_name": [
            "The 0.full_name field is required."
        ],
        "0.age": [
            "The 0.age field is required."
        ],
        "0.date": [
            "The 0.date field is required."
        ]
    }
}
```
{% endswagger-response %}
{% endswagger %}

## Update

To update the relationships between two people, you have to use the same query as to create a relationship while adding the id attribute of the relationship to modify in the body :

```json
[
    {
        'id': '',
        'field_id_1': 'value 1-1',
        'field_id_2': 'value 2-1',
        'date': '',
        ...
    },
    {
        'id': '',
        'field_id_1': 'value 1-2',
        'field_id_2': 'value 2-3',
        'date': '',
        ...
    }
]
```
