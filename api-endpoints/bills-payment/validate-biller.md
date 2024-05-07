# Validate Biller

Validate a biller details

```
POST {{BASE_URL}}/vace/v1/corporate/validate-biller
```

#### Body Parameters

<table><thead><tr><th width="177">Property</th><th width="158">Data Type</th><th width="279">Description</th><th width="158">Example</th><th>Required</th></tr></thead><tbody><tr><td>itemId</td><td>string or number</td><td>The bill item id you get from the List Bill Sub-Categories endpoint.</td><td>1465</td><td>Yes</td></tr><tr><td>customerId</td><td>string</td><td>The customer id for the bill. This can be for electricity or cableTv. For testing purposes, use <code>7032691481</code></td><td>"7032691481"</td><td>Yes</td></tr><tr><td>amount</td><td>number</td><td>The amount for the bill to be paid. This value comes alongside the bill sub-category details.</td><td>4125.00</td><td>Yes</td></tr><tr><td>billerId</td><td>string</td><td>The biller id. This comes alongside the bill sub-category details</td><td>"1465"</td><td>Yes</td></tr></tbody></table>

{% tabs %}
{% tab title="Node.js" %}
{% code lineNumbers="true" %}
```javascript
import Axios from 'axios';

// set the api url
const API_URL = `${BASE_URL}/vace/v1/corporate/validate-biller`;

// define request body
const data = {
    itemId: 1465,
    customerId: "7032691481",
    amount: 4150.00,
    billerId: "1465"
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
        "status": true,
        "billerCode": "N/A0",
        "billerItem": {
            "itemId": 1465,
            "amount": "4150.00",
            "name": ""
        },
        "customer": {
            "id": "7032691481",
            "name": "OMO QUEEN-SE2207",
            "network": "",
            "phoneNumber": ""
        },
        "currency": "NGN"
    },
    "message": "successful",
    "status": 200
}
```
{% endcode %}
{% endtab %}
{% endtabs %}
