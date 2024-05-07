# Verify Transaction

Get a single transaction on your Vacepay account

```
POST {{ BASE_URL }}/vace/v1/corporate/verify-transaction
```

#### Url Parameters

<table><thead><tr><th width="129">Property</th><th width="109">Data Type</th><th width="277">Description</th><th width="240">Example</th><th>Required</th></tr></thead><tbody><tr><td>reference</td><td>string</td><td>The transaction reference</td><td>"VPX014ba225-00914672"</td><td>Yes</td></tr><tr><td></td><td></td><td></td><td></td><td></td></tr></tbody></table>

{% tabs %}
{% tab title="Node.js" %}
{% code lineNumbers="true" %}
```javascript
import Axios from 'axios';

// set the api url
const API_URL = `${BASE_URL}/vace/v1/corporate/verify-transaction`;

// define request data
const data = {
    reference: "VPX014ba225-00914672"
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
        "status": "successful",
        "type": "debit",
        "reference": "VPX65f83c03-c11c4e54",
        "vaceRef": "VPX65f83c03-c11c4e54",
        "amount": 1000,
        "currency": "NGN",
        "description": "Wallet transfer from Blueray Solutions Limited to 0252872742|AGBELEYE OLUWATOBI EMMANUEL",
        "feature": "wallet-transfer",
        "fee": 100,
        "ipAddress": "",
        "bank": {
            "name": "",
            "accountName": "",
            "accountNo": "",
            "bankCode": ""
        },
        "card": {
            "brand": "",
            "cardBin": "",
            "cardLast": "",
            "expiryMonth": "",
            "expiryYear": ""
        },
        "customer": {
            "firstName": "AGBELEYE OLUWATOBI EMMANUEL",
            "lastName": "AGBELEYE OLUWATOBI EMMANUEL",
            "email": "",
            "phoneNumber": "",
            "phoneCode": "",
            "city": "",
            "state": "",
            "accountNo": "0252872742",
            "sourceAccount": "Vacepay"
        },
        "vasData": {
            "ref": "",
            "type": "",
            "network": "",
            "phoneNumber": "",
            "billerCode": "",
            "billerName": "",
            "hasToken": false,
            "token": ""
        },
        "createdAt": "2024-01-12T21:12:30.629Z",
        "updatedAt": "2024-01-12T21:12:59.204Z"
    },
    "message": "successful",
    "status": 200
}
```
{% endcode %}
{% endtab %}
{% endtabs %}
