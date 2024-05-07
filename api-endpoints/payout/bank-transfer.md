# Bank Transfer

Send money to a Nigerian bank account.

```
POST {{ BASE_URL }}/vace/v1/corporate/transfer
```

#### Body Parameters

<table><thead><tr><th width="158">Property</th><th width="126">Data Type</th><th width="279">Description</th><th width="173">Example</th><th>Required</th></tr></thead><tbody><tr><td>type</td><td>string</td><td>The type of transfer you want to initiate. The value here will be <code>account</code></td><td>"account"</td><td>Yes</td></tr><tr><td>amount</td><td>number</td><td>The amount you want to transfer</td><td>2000</td><td>Yes</td></tr><tr><td>bank</td><td>object</td><td>The bank details object. This should contain the <code>accountNo</code> and <code>bankCode</code></td><td>N/A</td><td>Yes</td></tr><tr><td>bank.accountNo</td><td>string</td><td>The recipient account number</td><td>"0252872742"</td><td>Yes</td></tr><tr><td>bank.bankCode</td><td>string</td><td>The sort code of the recipient bank. You can get list of banks using the List Banks endpoint.</td><td>"058"</td><td>Yes</td></tr><tr><td>pin</td><td>string</td><td>Your 4-digit transaction PIN</td><td>"0000"</td><td>Yes</td></tr><tr><td>reference</td><td>string</td><td>Your preferred transaction reference</td><td>"txref_09376384GH"</td><td>No</td></tr></tbody></table>

{% tabs %}
{% tab title="Node.js" %}
{% code lineNumbers="true" %}
```javascript
import Axios from 'axios';

// set the api url
const API_URL = `${BASE_URL}/vace/v1/corporate/transfer`;

// define request data
const data = {
    type: "account",
    amount: 2000,
    bank: {
        accountNo: "0252872742",
        bankCode: "058"
    },
    pin: "0000",
    reference: "txref_09376384GH"
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
        "reference": "VPXb9d80447-540c41f9",
        "accountName": "AGBELEYE OLUWATOBI EMMANUEL",
        "accountNo": "0252872742",
        "bankCode": "058",
        "amount": 2000
    },
    "message": "successful",
    "status": 200
}
```
{% endcode %}
{% endtab %}
{% endtabs %}
