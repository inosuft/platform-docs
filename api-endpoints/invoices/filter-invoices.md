# Filter Invoices

Get a list of your invoices on Vacepay.&#x20;

```
POST {{ BASE_URL }}/vace/v1/corporate/filter-invoices
```

#### Optional Query Parameters

<table><thead><tr><th>Property</th><th width="158">Data Type</th><th width="279">Description</th><th>Example</th></tr></thead><tbody><tr><td>limit</td><td>string</td><td>Number of records per page</td><td>50</td></tr><tr><td>page</td><td>string</td><td>Page number to view</td><td>1</td></tr><tr><td>order</td><td>string</td><td>Arrangement of records in descending or ascending order</td><td>"asc" or "desc"</td></tr></tbody></table>

#### Body Parameters

<table><thead><tr><th width="135">Property</th><th width="158">Data Type</th><th width="283">Description</th><th width="107">Example</th><th width="178">Required</th></tr></thead><tbody><tr><td>isEnabled</td><td>boolean</td><td>Specify filter value for the enabled status of the product</td><td>true</td><td>Yes, if no other field is specified</td></tr><tr><td>status</td><td>string</td><td>Status of the invoice</td><td>"pending"</td><td>Yes if no other field is specified</td></tr></tbody></table>

{% tabs %}
{% tab title="Node.js" %}
{% code lineNumbers="true" %}
```javascript
import Axios from 'axios';

// set the api url
const API_URL = `${BASE_URL}/vace/v1/corporate/filter-invoices`;

// define request body
const data = {
    isEnabled: true,
    type: "percentage"
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
    "total": 1,
    "pagination": {},
    "data": [
        {
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
        }
    ],
    "message": "successful",
    "status": 200
}
```
{% endcode %}
{% endtab %}
{% endtabs %}
