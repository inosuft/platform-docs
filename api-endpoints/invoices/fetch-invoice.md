# Fetch Invoice

Get a single product on your Vacepay account

```
GET {{ BASE_URL }}/vace/v1/corporate/invoice/{code}
```

#### Url Parameters

<table><thead><tr><th width="129">Property</th><th>Data Type</th><th width="277">Description</th><th width="200">Example</th><th>Required</th></tr></thead><tbody><tr><td>code</td><td>string</td><td>The invoice code</td><td>"VPIFFEE52E2"</td><td>Yes</td></tr><tr><td></td><td></td><td></td><td></td><td></td></tr></tbody></table>

{% tabs %}
{% tab title="Node.js" %}
{% code lineNumbers="true" %}
```javascript
import Axios from 'axios';

// set the api url
const API_URL = `${BASE_URL}/vace/v1/corporate/invoice/${code}`;

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
    "data": {
        "code": "VPIB3E319FB",
        "name": "NANST-INV",
        "number": "NANST-00124",
        "status": "pending",
        "link": "https://staging-web.vacepay.com/invoice/VPIB3E319FB",
        "VAT": {
            "title": "TAX",
            "type": "percentage",
            "value": 5
        },
        "summary": {
            "subtotal": 4001.98,
            "partialAmount": 0,
            "totalAmount": 4202.08
        },
        "description": "Invoice for nanst limited",
        "isEnabled": true,
        "inflow": {
            "value": 0,
            "count": 0
        },
        "items": [
            {
                "label": "ITMKFMFWS",
                "name": "Brown D&G Bag",
                "price": 2000.99,
                "quantity": 2,
                "total": 4001.98
            }
        ],
        "dueAt": {
            "date": "2024-01-28",
            "time": "00:30:45",
            "ISO": "2024-01-28T00:30:45.000Z"
        },
        "issuedAt": {
            "date": "2024-01-13",
            "time": "18:31:23",
            "ISO": "2024-01-13T18:31:23.094Z"
        },
        "paymentLink": "",
        "recipient": {
            "type": "business",
            "businessName": "NANST Solutions Limited",
            "firstName": "Oluwatobi",
            "lastName": "Immanuel",
            "email": "nanst@gmail.com",
            "phoneNumber": "08137031202",
            "phoneCode": "+234",
            "countryCode": "NG",
            "address": "Alausa, Ikeja Lagos.",
            "city": "Ikeja",
            "state": "Lagos"
        },
        "createdAt": "2024-01-13T18:31:23.061Z",
        "updatedAt": "2024-01-13T18:31:23.113Z"
    },
    "message": "successful",
    "status": 200
}
```
{% endcode %}
{% endtab %}
{% endtabs %}