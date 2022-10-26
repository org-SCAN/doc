# Relations

## Add relations

This query allows the addition of a relation between two already stored persons. The body must be in json format and follow the following structure :

```json
[
  {
    "from": "",
    "to": "",
    "relation": "",
    "date": "",
    "detail": ""
  },
  {
    "from": "",
    "to": "",
    "relation": "",
    "date": "",
    "detail": ""
  }
]
```

{% hint style="success" %}
The server responds by listing the ids of the relationships created
{% endhint %}

{% swagger method="post" path="/links" baseUrl="https://app.netw4ppl.tech/api" summary="Add relations" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="header" name="Application-id" required="true" %}

{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" required="true" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" type="json" %}
The json should match 

[#add-update-a-relation](relations.md#add-update-a-relation "mention")


{% endswagger-parameter %}

{% swagger-response status="201: Created" description="Returns the list of relation ID" %}
```json
[
    "727bf5e9-1c87-42b2-ba44-4b020520eb9f"
]
```
{% endswagger-response %}

{% swagger-response status="422: Unprocessable Entity" description="" %}
```javascript
{
    "message": "The 0.from must be a valid UUID.",
    "errors": {
        "0.from": [
            "The 0.from must be a valid UUID."
        ]
    }
}
```
{% endswagger-response %}
{% endswagger %}

## Update relations

To update the relationships between two people, you have to use the same query as to create a relationship while adding the id attribute of the relationship to modify in the body :

```json
[
  {
    "id": "",
    "from": "",
    "to": "",
    "relation": "",
    "date": "",
    "detail": ""
  },
  {
    "id": "",
    "from": "",
    "to": "",
    "relation": "",
    "date": "",
    "detail": ""
  }
]
```

The server responds by listing the ids of the relationships created
