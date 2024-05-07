# Fetch Subaccount

Get a single product on your Vacepay account

```
GET {{ BASE_URL }}/vace/v1/corporate/subaccount/{code}
```

#### Url Parameters

<table><thead><tr><th width="129">Property</th><th>Data Type</th><th width="277">Description</th><th width="200">Example</th><th>Required</th></tr></thead><tbody><tr><td>code</td><td>string</td><td>The subaccount code</td><td>"VSA_6yhyzzkcHc"</td><td>Yes</td></tr><tr><td></td><td></td><td></td><td></td><td></td></tr></tbody></table>

{% tabs %}
{% tab title="Node.js" %}
{% code lineNumbers="true" %}
```javascript
import Axios from 'axios';

// set the api url
const API_URL = `${BASE_URL}/vace/v1/corporate/subaccount/${code}`;

// make request using axios
Axios({
    method: "GET",
    url: `${API_URL}`,
    headers: {
        lg: 'en',
        ch: 'web'
        Authorization: `Bearer ${API_KEY}`,
        'Content-Type': 'application/json',
    }
}).then((resp) => {
    console.log(resp)
}).catch((err) => {
    console.log(err)
})
```
{% endcode %}
{% endtab %}

{% tab title="Response" %}
{% code lineNumbers="true" %}
```javascript
{
    "error": false,
    "errors": [],
    "data": {
        "code": "VSA_6yhyzzkcHc",
        "description": "Concreap subaccount for vacepay",
        "isEnabled": true,
        "name": "Concreap",
        "email": "hello@concreap.com",
        "phoneNumber": "02137031202",
        "phoneCode": "+234",
        "inflow": {
            "value": 0,
            "count": 0
        },
        "split": {
            "value": 10.05,
            "type": "percentage"
        },
        "bank": {
            "accountNo": "0125318431",
            "acccountName": "CONCREAP TECHNOLOGY SOLUTIONS LIMITED",
            "bankCode": "035",
            "name": "Wema Bank"
        },
        "slug": "concreap",
        "createdAt": "2024-01-12T03:00:09.675Z",
        "updatedAt": "2024-01-12T03:00:09.675Z"
    },
    "message": "successful",
    "status": 200
}
```
{% endcode %}
{% endtab %}
{% endtabs %}
