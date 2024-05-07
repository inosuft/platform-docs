# Change Settlement Bank

Add a bank account to your Vacepay account.

```
POST {{ BASE_URL }}/vace/v1/corporate/change-settlement-bank
```

#### Body Parameters

<table><thead><tr><th width="158">Property</th><th width="126">Data Type</th><th width="279">Description</th><th width="173">Example</th><th>Required</th></tr></thead><tbody><tr><td>bankCode</td><td>string</td><td>The bank sort code. Use the List Banks endpoint to get list of banks and their codes</td><td>"035"</td><td>Yes</td></tr><tr><td>accountNo</td><td>string</td><td>Your bank account number</td><td>"0125089414"</td><td>Yes</td></tr></tbody></table>

{% tabs %}
{% tab title="Node.js" %}
{% code lineNumbers="true" %}
```javascript
import Axios from 'axios';

// set the api url
const API_URL = `${BASE_URL}/vace/v1/corporate/change-settlement-bank`;

// define request data
const data = {
    bankCode: "035",
    accountNo: "0125089414"
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
        "name": "Wema Bank",
        "accountNo": "0125089414",
        "accountName": "INOSUFT TECHNOLOGIES LIMITED",
        "bankCode": "035",
        "updatedAt": "2024-01-09T10:41:24.645Z"
    },
    "message": "successful",
    "status": 200
}
```
{% endcode %}
{% endtab %}
{% endtabs %}
