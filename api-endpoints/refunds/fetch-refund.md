# Fetch Refund

Get a single product on your Vacepay account

```
GET {{ BASE_URL }}/vace/v1/corporate/refund/{code}
```

#### Url Parameters

<table><thead><tr><th width="129">Property</th><th>Data Type</th><th width="277">Description</th><th width="200">Example</th><th>Required</th></tr></thead><tbody><tr><td>code</td><td>string</td><td>The refund code</td><td>"VPF-19a0a4fc"</td><td>Yes</td></tr><tr><td></td><td></td><td></td><td></td><td></td></tr></tbody></table>

{% tabs %}
{% tab title="Node.js" %}
{% code lineNumbers="true" %}
```javascript
import Axios from 'axios';

// set the api url
const API_URL = `${BASE_URL}/vace/v1/corporate/refund/${code}`;

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
        "code": "VPF-19a0a4fc",
        "amount": 1000,
        "option": "instant",
        "reason": "Transaction was successful but needs to be refunded",
        "status": "successful",
        "type": "full",
        "paidAt": {
            "day": "2024-01-14",
            "time": "07:13:00",
            "ISO": "2024-01-14T07:13:00.933Z"
        },
        "bank": {
            "accountName": "AGBELEYE OLUWATOBI EMMANUEL",
            "accountNo": "0252872742",
            "bankCode": "058",
            "name": "guaranty"
        },
        "createdAt": "2024-01-14T07:12:12.721Z",
        "updatedAt": "2024-01-14T07:13:00.943Z",
        "transaction": {
            "reference": "VPX0c94e97c-b5534eaf",
            "amount": 1000,
            "fee": 100,
            "feature": "wallet-transfer",
            "createdAt": "2024-01-12T20:23:59.787Z"
        }
    },
    "message": "successful",
    "status": 200
}
```
{% endcode %}
{% endtab %}
{% endtabs %}
