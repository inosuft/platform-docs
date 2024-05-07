---
description: >-
  This page describes how you make a call to our APIs. The header properties and
  the required parameters needed to make a successful API call.
---

# 🎾 Authentication

Every API endpoint requires some form of authentication using a bearer token header and two major header parameters. The key required for each request is your API Key.\
\
To enable communication between your application and Vacepay, you'll need your API Key. Vacepay authenticates every request your application makes with your API key. Generally, every corporate account comes with a single API Key  for Staging and Live accounts.\
\
Your API key is required for accessing any financial data and can be used to make any API call on your account. Your key should never be shared on any client-side code or exposed on any application that is not yours. Treat them like any other password. And, if for any reason you believe your API key has been compromised simply reset them by generating new key. You can generate new API key from your dashboard.\
\
For every endpoint, you must specify the headers below.

| Property      | Value                           | Description                                                                                      |
| ------------- | ------------------------------- | ------------------------------------------------------------------------------------------------ |
| Content-Type  | "application/javascript"        | Request content type                                                                             |
| lg            | "en"                            | Language Type. This value should be "en"                                                         |
| ch            | "web"                           | Channel Type. This is defaulted to "web" but can be any of "web", "mobile", "watch" or "desktop" |
| Authorization | "Bearer \{{ YOUR\_API\_KEY \}}" | Token for authourization                                                                         |

### Obtaining your API Key

Your API key is always available on your dashboard. To find your API key,

* Login to your Vacepay account
* Navigate to "Settings" on the side menu
* Click "Webhook & API Key" on the sub-menu
* In the Vacepay Webhook & API Key section, you’d see both your API Key and Webhook configuration section. You'll also see a button to generate a new API Key and make changes to your webhook.

{% hint style="info" %}
The API Keys for TEST ( i.e. Staging ) mode and LIVE mode are different. So you need to always ensure that you do not misuse the keys when you switch between modes.
{% endhint %}

<figure><img src="../.gitbook/assets/Screenshot 2024-01-07 at 5.38.40 PM (2).png" alt=""><figcaption><p>Webhook &#x26; API Key Section on Vacepay Dashboard</p></figcaption></figure>

### Generating New API Key

You should always keep your API keys safe and protect your account. However, in the event where your API keys have been compromised, you can easily generate new API keys. Simply click the "Re-Generate Key" button under the "Your API Key" section on the Webhook & API Key page.

{% hint style="info" %}
Once you generate new API keys, the old keys become void - you can no longer use them to make API calls. Make sure to update your application to use the newly generated keys.
{% endhint %}

<figure><img src="../.gitbook/assets/Screenshot 2024-01-07 at 5.38.40 PM (1).png" alt=""><figcaption><p>Generate new API key using the button in the screenshot</p></figcaption></figure>

If you fail to include your key when making an API request or provide an incorrect key, Vacepay will respond with an error message. Check sample error below

{% tabs %}
{% tab title="Invalid API Key" %}
```javascript
{
    "error": true,
    "errors": [
        "user is not authorized to access this route"
    ],
    "data": {},
    "message": "Error",
    "status": 401
}
```
{% endtab %}

{% tab title="Second Tab" %}

{% endtab %}
{% endtabs %}
