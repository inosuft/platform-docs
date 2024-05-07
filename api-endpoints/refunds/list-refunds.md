# List Refunds

Get a list of refunds on your Vacepay account.&#x20;

```
GET {{ BASE_URL }}/vace/v1/corporate/refunds
```

#### Optional Query Parameters

<table><thead><tr><th>Property</th><th width="158">Data Type</th><th width="279">Description</th><th>Example</th></tr></thead><tbody><tr><td>limit</td><td>string</td><td>Number of records per page</td><td>50</td></tr><tr><td>page</td><td>string</td><td>Page number to view</td><td>1</td></tr><tr><td>order</td><td>string</td><td>Arrangement of records in descending or ascending order</td><td>"asc" or "desc"</td></tr></tbody></table>

{% tabs %}
{% tab title="Node.js" %}
{% code lineNumbers="true" %}
```javascript
import Axios from 'axios';

// set the api url
const API_URL = `${BASE_URL}/vace/v1/corporate/refunds`;

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
    "count": 1,
    "total": 3,
    "pagination": {
        "next": {
            "page": 2,
            "limit": 1
        }
    },
    "data": [
        {
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
                "name": "Guaranty Trust Bank"
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
        }
    ],
    "message": "successful",
    "status": 200
}
```
{% endcode %}
{% endtab %}
{% endtabs %}
