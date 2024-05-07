# Filter Payment Links

Get a list of your subaccounts on Vacepay.&#x20;

```
POST {{ BASE_URL }}/vace/v1/corporate/filter-payments
```

#### Optional Query Parameters

<table><thead><tr><th>Property</th><th width="158">Data Type</th><th width="279">Description</th><th>Example</th></tr></thead><tbody><tr><td>limit</td><td>string</td><td>Number of records per page</td><td>50</td></tr><tr><td>page</td><td>string</td><td>Page number to view</td><td>1</td></tr><tr><td>order</td><td>string</td><td>Arrangement of records in descending or ascending order</td><td>"asc" or "desc"</td></tr></tbody></table>

#### Body Parameters

<table><thead><tr><th width="135">Property</th><th width="158">Data Type</th><th width="283">Description</th><th width="107">Example</th><th width="156">Required</th><th></th></tr></thead><tbody><tr><td>isEnabled</td><td>boolean</td><td>Specify filter value for the enabled status of the payment link</td><td>true</td><td>Yes, if no other field is specified</td><td></td></tr><tr><td>type</td><td>string</td><td>The type for a payment link. This can be <code>fixed</code> or <code>dynamic</code></td><td>"fixed"</td><td>Yes if no other field is specified</td><td></td></tr><tr><td>feature</td><td>string</td><td>The feature of the payment link. This can either be <code>request</code>, <code>product</code> or <code>invoice</code></td><td>"request"</td><td>Yes if no other field is specified</td><td></td></tr></tbody></table>

{% tabs %}
{% tab title="Node.js" %}
{% code lineNumbers="true" %}
```javascript
import Axios from 'axios';

// set the api url
const API_URL = `${BASE_URL}/vace/v1/corporate/filter-subaccounts`;

// define request body
const data = {
    isEnabled: true,
    type: "fixed",
    feature: "request"
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
            "name": "Crowd Fund School",
            "slug": "crowd-fund",
            "link": "https://staging-web.vacepay.com/link/crowd-fund",
            "qrcode": "https://storage.googleapis.com/concreap-buckets/qrcode-4ebc1b81",
            "redirectUrl": "",
            "feature": "request",
            "type": "fixed",
            "isEnabled": true,
            "message": "Thank you for your payment",
            "description": "",
            "amount": 5000,
            "totalAmount": 15000,
            "createdAt": "2024-01-13T05:39:48.624Z",
            "updatedAt": "2024-01-13T06:12:53.060Z",
            "options": {
                "card": true,
                "transfer": true,
                "bank": false,
                "ussd": false,
                "bankQR": false
            }
        }
    ],
    "message": "successful",
    "status": 200
}
```
{% endcode %}
{% endtab %}
{% endtabs %}
