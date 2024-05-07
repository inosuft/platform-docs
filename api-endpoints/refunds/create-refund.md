# Create Refund

Create a refund on a transaction

```
POST {{ BASE_URL }}/vace/v1/corporate/refund
```

#### Body Parameters

<table><thead><tr><th width="129">Property</th><th width="109">Data Type</th><th width="277">Description</th><th width="240">Example</th><th width="186">Required</th></tr></thead><tbody><tr><td>reference</td><td>string</td><td>The transaction reference</td><td>"VPX014ba225-00914672"</td><td>Yes</td></tr><tr><td>option</td><td>string</td><td>The reund option type. This can be <code>instant</code> or <code>request</code></td><td>"instant"</td><td>Yes</td></tr><tr><td>reason</td><td>string</td><td>The reason for refund</td><td>"Quick refund"</td><td>Yes</td></tr><tr><td>type</td><td>string</td><td>The type of refund. This can be <code>full</code> or <code>partial</code></td><td>"full"</td><td>Yes</td></tr><tr><td>amount</td><td>number</td><td>amount to be refunded</td><td>100</td><td>Only if refund type is partial</td></tr><tr><td>bank</td><td>object</td><td>An object that hold bank details if refund type is instant</td><td>N/A</td><td>Only if refund type is instant</td></tr><tr><td>bank.accountNo</td><td>string</td><td>Bank account number to refund to</td><td>"0252872742"</td><td>Yes</td></tr><tr><td>bank.bankCode</td><td>string</td><td>Bank sort code to refund to. Get sort code from the List Banks endpoint</td><td>"058"</td><td>Yes</td></tr><tr><td>pin</td><td>string</td><td>Your 4-digit transaction pin</td><td>"0000"</td><td>Yes</td></tr></tbody></table>

{% tabs %}
{% tab title="Node.js" %}
{% code lineNumbers="true" %}
```javascript
import Axios from 'axios';

// set the api url
const API_URL = `${BASE_URL}/vace/v1/corporate/refund`;

// define request data
const data = {
    reference: "VPX65f83c03-c11c4e54",
    option: "instant",
    reason: "Transaction was successful but needs to be refunded",
    type: "full",
    amount: 0,
    bank: {
        accountNo: "0252872742",
        bankCode: "058"
    },
    pin: "3662"
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
        "code": "VPF-19a0a4fc",
        "amount": 1000,
        "option": "instant",
        "reason": "Transaction was successful but needs to be refunded",
        "status": "pending",
        "type": "full",
        "paidAt": {
            "day": "2024-01-14",
            "time": "07:12:13",
            "ISO": "2024-01-14T07:12:13.356Z"
        },
        "bank": {
            "accountNo": "0252872742",
            "accountName": "AGBELEYE OLUWATOBI EMMANUEL",
            "bankCode": "058",
            "legalName": "Guaranty Trust Bank",
            "name": "guaranty"
        },
        "createdAt": "2024-01-14T07:12:12.721Z",
        "updatedAt": "2024-01-14T07:12:13.360Z",
        "transaction": {
            "reference": "VPX0c94e97c-b5534eaf",
            "amount": 1000,
            "fee": 100,
            "feature": "wallet-transfer",
            "createdAt": "2024-01-12T20:23:59.787Z"
        }
    },
    "message": "successful",
    "status": 200
}
```
{% endcode %}
{% endtab %}
{% endtabs %}
