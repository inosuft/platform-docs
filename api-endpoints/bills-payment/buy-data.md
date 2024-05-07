# Buy Data

Buy data for various mobile services

```
POST {{ BASE_URL }}/vace/v1/corporate/data
```

#### Body Parameters

<table><thead><tr><th width="158">Property</th><th width="126">Data Type</th><th width="279">Description</th><th width="173">Example</th><th>Required</th></tr></thead><tbody><tr><td>amount</td><td>number</td><td>The airtime amount you want to buy</td><td>2000</td><td>Yes</td></tr><tr><td>phoneNumber</td><td>string</td><td>The recipient 11-digit phone number.</td><td>"08137031202"</td><td>Yes</td></tr><tr><td>phoneCode</td><td>string</td><td>The recipient phone number country call code.</td><td>"+234"</td><td>Yes</td></tr><tr><td>network</td><td>string</td><td>The network label from using the List Networks endpoint.</td><td>"mtn"</td><td>Yes</td></tr><tr><td>pin</td><td>string</td><td>Your 4-digit transaction PIN</td><td>"0000"</td><td>Yes</td></tr><tr><td>dataId</td><td>string or number</td><td>The mobile data plan id from the List Mobile Data Plans endpoint.</td><td>1400</td><td></td></tr><tr><td>reference</td><td>string</td><td>Your preferred transaction reference</td><td>"txref_0937638BCC"</td><td>No</td></tr></tbody></table>

{% tabs %}
{% tab title="Node.js" %}
{% code lineNumbers="true" %}
```javascript
import Axios from 'axios';

// set the api url
const API_URL = `${BASE_URL}/vace/v1/corporate/data`;

// define request data
const data = {
    amount: 1000,
    phoneNumber: "08137031202",
    phoneCode: "+234"
    network: "mtn",
    pin: "0000",
    dataId: 1400,
    reference: "txref_09376384BCC"
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
```json
{
    "error": false,
    "errors": [],
    "data": {
        "amount": 100,
        "reference": "VPX387a2041-854049c3",
        "balance": 24839
    },
    "message": "successful",
    "status": 200
}
```
{% endcode %}
{% endtab %}
{% endtabs %}
