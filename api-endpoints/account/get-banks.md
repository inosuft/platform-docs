# Get Banks

Get list of banks added to your Vacepay account

```
GET {{BASE_URL}}/vace/v1/corporate/banks
```

#### Optional Query Parameters

<table><thead><tr><th>Property</th><th width="158">Data Type</th><th width="279">Description</th><th>Example</th></tr></thead><tbody><tr><td>limit</td><td>string</td><td>Number of records per page</td><td>50</td></tr><tr><td>page</td><td>string</td><td>Page number to view</td><td>1</td></tr><tr><td>order</td><td>string</td><td>Arrangement of records in descending or ascending order</td><td>"asc" or "desc"</td></tr><tr><td>select</td><td>string</td><td>properties of each record to select and display. separate by comma.</td><td>name,code,accountName,accountNo</td></tr></tbody></table>

{% tabs %}
{% tab title="Node.js" %}
{% code lineNumbers="true" %}
```javascript
import Axios from 'axios';

// set the api url
const API_URL = `${BASE_URL}/vace/v1/corporate/banks`;

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
```json
{
    "error": false,
    "errors": [],
    "count": 2,
    "total": 3,
    "pagination": {},
    "data": [
        {
            "accountName": "INOSUFT TECHNOLOGIES LIMITED",
            "accountNo": "0125089414",
            "code": "035",
            "country": "nigeria",
            "currency": "NGN",
            "name": "Wema Bank",
            "type": "nuban"
        },
        {
            "accountName": "AGBELEYE OLUWATOBI EMMANUEL",
            "accountNo": "0252872742",
            "code": "058",
            "country": "nigeria",
            "currency": "NGN",
            "name": "Guaranty Trust Bank",
            "type": "nuban"
        }
    ],
    "message": "successful",
    "status": 200
}
```
{% endcode %}
{% endtab %}
{% endtabs %}
