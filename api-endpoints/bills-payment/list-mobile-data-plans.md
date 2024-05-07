# List Mobile Data Plans

Get a list of bill subcategories from a bill category Vacepay supports

```
POST {{BASE_URL}}/vace/v1/corporate/mobile-data-plans
```

#### Body Parameters

<table><thead><tr><th width="177">Property</th><th width="158">Data Type</th><th width="279">Description</th><th width="158">Example</th><th>Required</th></tr></thead><tbody><tr><td>networkName</td><td>string</td><td>The label of the network you get from calling the List Mobile Networks endpoint.</td><td>"mtn"</td><td>Yes</td></tr><tr><td>phoneNumber</td><td>string</td><td>The 11-digit phone number of the data recipient.</td><td>"08137031202"</td><td>Yes</td></tr></tbody></table>

{% tabs %}
{% tab title="Node.js" %}
{% code lineNumbers="true" %}
```javascript
import Axios from 'axios';

// set the api url
const API_URL = `${BASE_URL}/vace/v1/corporate/bill-sub-categories`;

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
    "data": [
        {
            "dataBundle": {
                "bundle": "100MB Daily for Daily - Daily",
                "amount": "100.00",
                "validity": "Daily",
                "currency": "NGN",
                "network": "mtn",
                "dataId": 1400
            },
            "vasCode": "VF01",
            "countryCode": "NG"
        },
        {
            "dataBundle": {
                "bundle": "200MB 3Day Plan for Daily - Daily",
                "amount": "200.00",
                "validity": "Daily",
                "currency": "NGN",
                "network": "mtn",
                "dataId": 1401
            },
            "vasCode": "VF01",
            "countryCode": "NG"
        },
    ],
    "message": "successful",
    "status": 200
}

```
{% endcode %}
{% endtab %}
{% endtabs %}
