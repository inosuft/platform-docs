# Withdraw Money

Send money to a NGN bank account already added to your Vacepay account.

```
POST {{ BASE_URL }}/vace/v1/corporate/withdraw
```

#### Body Parameters

<table><thead><tr><th width="158">Property</th><th width="126">Data Type</th><th width="279">Description</th><th width="173">Example</th><th>Required</th></tr></thead><tbody><tr><td>amount</td><td>number</td><td>The amount you want to withdraw</td><td>2000</td><td>Yes</td></tr><tr><td>accountNo</td><td>string</td><td>An account number from the list of banks you already added to your Vacepay account. You can get list of your banks using the <a href="https://vace-docs.gitbook.io/corporate/api-endpoints/account/get-banks">Get Banks</a> endpoint.</td><td>N/A</td><td>Yes</td></tr><tr><td>pin</td><td>string</td><td>Your 4-digit transaction PIN</td><td>"0000"</td><td>Yes</td></tr><tr><td>reference</td><td>string</td><td>Your preferred transaction reference</td><td>"txref_09376384ACC"</td><td>No</td></tr></tbody></table>

{% tabs %}
{% tab title="Node.js" %}
{% code lineNumbers="true" %}
```javascript
import Axios from 'axios';

// set the api url
const API_URL = `${BASE_URL}/vace/v1/corporate/withdraw`;

// define request data
const data = {
    amount: 2000,
    accountNo: "0252872742"
    pin: "0000",
    reference: "txref_09376384ACC"
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
        "accountNo": "0252872742",
        "accountName": "AGBELEYE OLUWATOBI EMMANUEL",
        "bank": {
            "name": "Guaranty Trust Bank",
            "bankCode": "058"
        },
        "amount": 1000,
        "reference": "VPX0d8e8f0d-32f54398"
    },
    "message": "successful",
    "status": 200
}
```
{% endcode %}
{% endtab %}
{% endtabs %}
