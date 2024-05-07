# List Payment Link Transactions

Get a list of your payment links on Vacepay.&#x20;

```
GET {{ BASE_URL }}/vace/v1/corporate/payment-transactions/{{slug}}
```

#### Optional Query Parameters

<table><thead><tr><th>Property</th><th width="158">Data Type</th><th width="279">Description</th><th>Example</th></tr></thead><tbody><tr><td>limit</td><td>string</td><td>Number of records per page</td><td>50</td></tr><tr><td>page</td><td>string</td><td>Page number to view</td><td>1</td></tr><tr><td>order</td><td>string</td><td>Arrangement of records in descending or ascending order</td><td>"asc" or "desc"</td></tr></tbody></table>

{% tabs %}
{% tab title="Node.js" %}
{% code lineNumbers="true" %}
```javascript
import Axios from 'axios';

// set the api url
const API_URL = `${BASE_URL}/vace/v1/corporate/payment-transactions/${slug}`;

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
    "count": 1,
    "total": 13,
    "pagination": {
        "next": {
            "page": 2,
            "limit": 1
        }
    },
    "data": [
        {
            "status": "successful",
            "type": "credit",
            "reference": "VPXf6126884-7bfc4b35",
            "vaceRef": "VPXf6126884-7bfc4b35",
            "amount": 5000,
            "currency": "NGN",
            "description": "incoming payment of NGN5,000 to Blueray Solutions Limited via payment link",
            "feature": "payment-link",
            "fee": 200,
            "ipAddress": "172.31.63.134",
            "bank": {
                "name": "",
                "accountName": "",
                "accountNo": "",
                "bankCode": ""
            },
            "card": {
                "brand": "verve",
                "cardBin": "507850",
                "cardLast": "7812",
                "expiryMonth": "01",
                "expiryYear": "2025"
            },
            "customer": {
                "firstName": "Oluwatobi",
                "lastName": "Immanuel",
                "email": "tobi@test.com",
                "phoneNumber": "08137031202",
                "phoneCode": "+234",
                "city": "",
                "state": "",
                "accountNo": "",
                "sourceAccount": ""
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
            "createdAt": "2024-01-13T06:12:47.241Z",
            "updatedAt": "2024-01-13T06:12:53.141Z"
        }
    ],
    "message": "successful",
    "status": 200
}
```
{% endcode %}
{% endtab %}
{% endtabs %}
