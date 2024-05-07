# Pay Bill

Pay electricity or cableTv bills

```
POST {{ BASE_URL }}/vace/v1/corporate/bill
```

#### Body Parameters

<table><thead><tr><th width="158">Property</th><th width="126">Data Type</th><th width="279">Description</th><th width="173">Example</th><th>Required</th></tr></thead><tbody><tr><td>type</td><td>string</td><td>The label of the bill category you get from List Bill Categories endpoint.</td><td>"cable"</td><td>Yes</td></tr><tr><td>amount</td><td>number</td><td>The airtime amount you want to buy</td><td>2000</td><td>Yes</td></tr><tr><td>phoneNumber</td><td>string</td><td>The recipient 11-digit phone number.</td><td>"08137031202"</td><td>Yes</td></tr><tr><td>phoneCode</td><td>string</td><td>The recipient phone number country call code.</td><td>"+234"</td><td>Yes</td></tr><tr><td>itemId</td><td>string or number</td><td>The bill item id from the List Bill Sub-Categories endpoint</td><td>1465</td><td>Yes</td></tr><tr><td>customerId</td><td>string</td><td>The customer id for the specific bill category. Use <code>cable: 7032691481</code> for testing purposes</td><td>"7032691481"</td><td>Yes</td></tr><tr><td>billerId</td><td>string</td><td>The biller id you get from List Bill Sub-Categories endpoint</td><td>"1456"</td><td>Yes</td></tr><tr><td>pin</td><td>string</td><td>Your 4-digit transaction PIN</td><td>"0000"</td><td>Yes</td></tr><tr><td>reference</td><td>string</td><td>Your preferred transaction reference</td><td>"txref_0937638BCC"</td><td>No</td></tr></tbody></table>

{% tabs %}
{% tab title="Node.js" %}
{% code lineNumbers="true" %}
```javascript
import Axios from 'axios';

// set the api url
const API_URL = `${BASE_URL}/vace/v1/corporate/bill`;

// define request data
const data = {
    amount:4150.00,
    phoneNumber: "08137031202",
    phoneCode: "+234",
    itemId: 1465,
    pin:"3662",
    customerId: "7032691481",
    type: "cable",
    billerId: "1465",
    reference: "txref_0937638BCC"
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
        "amount": 4150,
        "reference": "VPXc3731ffc-7c9d4e3a"
    },
    "message": "successful",
    "status": 200
}
```
{% endcode %}
{% endtab %}
{% endtabs %}
