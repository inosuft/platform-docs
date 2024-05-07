# Search Transactions

Get a list of your transactions on your Vacepay account by searching.&#x20;

```
POST {{ BASE_URL }}/vace/v1/corporate/search-transactions
```

#### Optional Query Parameters

<table><thead><tr><th>Property</th><th width="158">Data Type</th><th width="279">Description</th><th>Example</th></tr></thead><tbody><tr><td>limit</td><td>string</td><td>Number of records per page</td><td>50</td></tr><tr><td>page</td><td>string</td><td>Page number to view</td><td>1</td></tr><tr><td>order</td><td>string</td><td>Arrangement of records in descending or ascending order</td><td>"asc" or "desc"</td></tr></tbody></table>

#### Body Parameters

<table><thead><tr><th width="135">Property</th><th width="158">Data Type</th><th width="283">Description</th><th width="155">Example</th><th>Required</th></tr></thead><tbody><tr><td>key</td><td>string</td><td>The search keyword. You can search using the reference or feature</td><td>"transfer"</td><td>Yes</td></tr><tr><td></td><td></td><td></td><td></td><td></td></tr></tbody></table>

{% tabs %}
{% tab title="Node.js" %}
{% code lineNumbers="true" %}
```javascript
import Axios from 'axios';

// set the api url
const API_URL = `${BASE_URL}/vace/v1/corporate/search-transactions`;

// define request body
const data = {
    key: "transfer"
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
    "count": 1,
    "total": 10,
    "pagination": {
        "next": {
            "page": 2,
            "limit": 1
        }
    },
    "data": [
        {
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
        }
    ],
    "message": "successful",
    "status": 200
}
```
{% endcode %}
{% endtab %}
{% endtabs %}