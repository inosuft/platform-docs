# Resolve Bank Account

Resolve a bank account number to enquire the account name

```
POST {{ BASE_URL }}/vace/v1/corporate/resolve
```

#### Body Parameters

<table><thead><tr><th width="135">Property</th><th width="114">Data Type</th><th width="283">Description</th><th width="190">Example</th><th>Required</th></tr></thead><tbody><tr><td>bankCode</td><td>string</td><td>The sort code of the bank. Get bank sort code from the List Banks endpoint</td><td>"058"</td><td>Yes</td></tr><tr><td>accountNo</td><td>string</td><td>The account number to resolve.</td><td>"0252872742"</td><td>Yes</td></tr></tbody></table>

{% tabs %}
{% tab title="Node.js" %}
{% code lineNumbers="true" %}
```javascript
import Axios from 'axios';

// set the api url
const API_URL = `${BASE_URL}/vace/v1/corporate/resolve`;

// define request body
const data = {
    bankCode: "058",
    accountNo: "0252872742"
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
```javascript
{
    "error": false,
    "errors": [],
    "data": {
        "accountNo": "0252872742",
        "accountName": "AGBELEYE OLUWATOBI EMMANUEL",
        "bankCode": "058",
        "bankName": "guaranty trust bank"
    },
    "message": "successful",
    "status": 200
}
```
{% endcode %}
{% endtab %}
{% endtabs %}
