# Get Beneficiaries

Get list of beneficiaries added to your Vacepay account.&#x20;

{% hint style="info" %}
Beneficiaries are automatically added to your vacepay account when you withdraw from your wallet to a NGN bank account.
{% endhint %}

```
GET {{ BASE_URL }}/vace/v1/corporate/beneficiaries
```

#### Optional Query Parameters

<table><thead><tr><th>Property</th><th width="158">Data Type</th><th width="279">Description</th><th>Example</th></tr></thead><tbody><tr><td>limit</td><td>string</td><td>Number of records per page</td><td>50</td></tr><tr><td>page</td><td>string</td><td>Page number to view</td><td>1</td></tr><tr><td>order</td><td>string</td><td>Arrangement of records in descending or ascending order</td><td>"asc" or "desc"</td></tr></tbody></table>

{% tabs %}
{% tab title="Node.js" %}
{% code lineNumbers="true" %}
```javascript
import Axios from 'axios';

// set the api url
const API_URL = `${BASE_URL}/vace/v1/corporate/beneficiaries`;

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
```json
{
    "error": false,
    "errors": [],
    "count": 1,
    "total": 1,
    "pagination": {},
    "data": [
        {
            "accountName": "AGBELEYE OLUWATOBI EMMANUEL",
            "accountNo": "0252872742",
            "code": "ddf990ff",
            "bankName": "guaranty trust bank",
            "bankCode": "058"
        }
    ],
    "message": "successful",
    "status": 200
}
```
{% endcode %}
{% endtab %}
{% endtabs %}
