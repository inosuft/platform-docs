# Validate Bill Status

Get the status of an already paid bill

```
POST {{BASE_URL}}/vace/v1/corporate/bill-status
```

#### Body Parameters

<table><thead><tr><th width="177">Property</th><th width="158">Data Type</th><th width="279">Description</th><th width="158">Example</th><th>Required</th></tr></thead><tbody><tr><td>reference</td><td>string</td><td>The transaction reference returned from performing a bill payment transaction</td><td>"VPX014ba225-00914672"</td><td>Yes</td></tr></tbody></table>

{% tabs %}
{% tab title="Node.js" %}
{% code lineNumbers="true" %}
```javascript
import Axios from 'axios';

// set the api url
const API_URL = `${BASE_URL}/vace/v1/corporate/bill-status`;

// define request body
const data = {
    reference: "VPX014ba225-00914672"
}

// make request using axios
Axios({
    method: "GET",
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
    "data": {
        "reference": "VPX014ba225-00914672",
        "status": "completed",
        "amount": "4150.00",
        "billerCode": "N/A0",
        "billerName": "OMO QUEEN-SE2207",
        "token": "",
        "customer": {},
        "category": {
            "mainCategory": "Cable TV Subscription",
            "subCategory": "GOTv (MultiChoice) Subscription Payment",
            "categoryId": 0,
            "name": ""
        },
        "createdAt": "2023-12-31T14:16:17.195332Z",
        "vasType": "Bills Payment"
    },
    "message": "successful",
    "status": 200
}
```
{% endcode %}
{% endtab %}
{% endtabs %}
