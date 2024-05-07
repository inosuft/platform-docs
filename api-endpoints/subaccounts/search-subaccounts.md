# Search Subaccounts

Get a list of your products on Vacepay.&#x20;

```
POST {{ BASE_URL }}/vace/v1/corporate/search-subaccounts
```

#### Optional Query Parameters

<table><thead><tr><th>Property</th><th width="158">Data Type</th><th width="279">Description</th><th>Example</th></tr></thead><tbody><tr><td>limit</td><td>string</td><td>Number of records per page</td><td>50</td></tr><tr><td>page</td><td>string</td><td>Page number to view</td><td>1</td></tr><tr><td>order</td><td>string</td><td>Arrangement of records in descending or ascending order</td><td>"asc" or "desc"</td></tr></tbody></table>

#### Body Parameters

<table><thead><tr><th width="135">Property</th><th width="158">Data Type</th><th width="283">Description</th><th width="155">Example</th><th>Required</th></tr></thead><tbody><tr><td>key</td><td>string</td><td>The search keyword. You can search with the subaccount name or code</td><td>"corporate"</td><td>Yes</td></tr><tr><td></td><td></td><td></td><td></td><td></td></tr></tbody></table>

{% tabs %}
{% tab title="Node.js" %}
{% code lineNumbers="true" %}
```javascript
import Axios from 'axios';

// set the api url
const API_URL = `${BASE_URL}/vace/v1/corporate/search-subaccounts`;

// define request body
const data = {
    key: "corporate"
}

// make request using axios
Axios({
    method: "POST",
    url: `${API_URL}`,
    headers: {
        lg: 'en',
        ch: 'web'
        Authorization: `Bearer ${API_KEY}`,
        'Content-Type': 'application/json',
    },
    data: data
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
    "count": 1,
    "total": 1,
    "pagination": {},
    "data": [
        {
            "code": "VSA_6yhyzzkcHc",
            "description": "Corporate NATS subaccount for vacepay",
            "isEnabled": true,
            "name": "Corporate NATS",
            "email": "hello@corporatenats.com",
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
            "slug": "corporate-nats",
            "createdAt": "2024-01-12T03:00:09.675Z",
            "updatedAt": "2024-01-12T03:00:09.675Z"
        }
    ],
    "message": "successful",
    "status": 200
}
```
{% endcode %}
{% endtab %}
{% endtabs %}
