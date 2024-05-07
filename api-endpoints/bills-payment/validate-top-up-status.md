# Validate Top-Up Status

Get the status of airtime or data top-up

```
POST {{BASE_URL}}/vace/v1/corporate/topup-status
```

#### Body Parameters

<table><thead><tr><th width="177">Property</th><th width="158">Data Type</th><th width="279">Description</th><th width="158">Example</th><th>Required</th></tr></thead><tbody><tr><td>reference</td><td>string</td><td>The transaction reference returned from performing a bill payment transaction</td><td>"VPX6ca6cefa-34c74eb4"</td><td>Yes</td></tr></tbody></table>

{% tabs %}
{% tab title="Node.js" %}
{% code lineNumbers="true" %}
```javascript
import Axios from 'axios';

// set the api url
const API_URL = `${BASE_URL}/vace/v1/corporate/topup-status`;

// define request body
const data = {
    reference: "VPX6ca6cefa-34c74eb4"
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
        "reference": "VPX6ca6cefa-34c74eb4",
        "status": "completed",
        "billerCode": "",
        "billerName": "",
        "hasToken": false,
        "token": "",
        "network": "mtn",
        "phoneNumber": "+2348137031202",
        "type": "airtime"
    },
    "message": "500 mtn airtime purchased via Softklin Services wallet",
    "status": 200
}
```
{% endcode %}
{% endtab %}
{% endtabs %}
