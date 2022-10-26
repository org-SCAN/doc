# 🔭 API

{% hint style="info" %}
**Good to know:** SCAN provides an API that allows you to fully interact with our application. You can create your own software to synchronize your data with SCAN!
{% endhint %}

## Get your personnal API keys

Your API requests are authenticated using API keys. Any request that doesn't include an API key will return an error.

You can generate get your API Token from your profile at any time.

## Application ID

The application ID is a unique token created by your application that identifies the application pushing the data. Each application ID must be different.

## Make your first request

{% hint style="info" %}
All requests given in this documentation use the endpoint _https://app.netw4ppl.tech_, make sure to replace the URL with your installation
{% endhint %}

To make your first request, send an authenticated request to the pets endpoint. You will get informations about the user you're logged with.

{% swagger baseUrl="https://app.netw4ppl.tech/api" method="get" path="/user" summary="Get user." %}
{% swagger-description %}
Get user informations.
{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" required="true" type="String" %}
Bearer <TOKEN>
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Application-id" required="true" %}
An application ID.
{% endswagger-parameter %}

{% swagger-response status="200" description="Pet successfully created" %}
```json
{
    "id": "a2a34d97-6de3-4a2e-b6a9-c44c72076e5d",
    "name": "Default user",
    "email": "dev@netw4ppl.tech",
    "email_verified_at": null,
    "crew_id": "b1d9649a-3431-4920-b05b-e8c4a75b0881",
    "profile_photo_path": null,
    "role_id": "ed1b8ae6-48c1-4190-90dc-4f3d91093e0b",
    "created_at": "2022-10-25T11:32:12.000000Z",
    "updated_at": "2022-10-25T11:32:12.000000Z",
    "deleted_at": null
}
```
{% endswagger-response %}

{% swagger-response status="401" description="Permission denied" %}

{% endswagger-response %}
{% endswagger %}
