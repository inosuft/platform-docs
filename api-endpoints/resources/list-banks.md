# List Banks

Get a list of your products on Vacepay.&#x20;

```
GET {{ BASE_URL }}/resource/v1/banks/list
```

#### Optional Query Parameters

<table><thead><tr><th>Property</th><th width="158">Data Type</th><th width="279">Description</th><th>Example</th></tr></thead><tbody><tr><td>limit</td><td>string</td><td>Number of records per page</td><td>50</td></tr><tr><td>page</td><td>string</td><td>Page number to view</td><td>1</td></tr><tr><td>order</td><td>string</td><td>Arrangement of records in descending or ascending order</td><td>"asc" or "desc"</td></tr></tbody></table>

{% tabs %}
{% tab title="Node.js" %}
{% code lineNumbers="true" %}
```javascript
import Axios from 'axios';

// set the api url
const API_URL = `${BASE_URL}/resource/v1/banks/list`;

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
    "count": 4,
    "total": 533,
    "pagination": {
        "next": {
            "page": 2,
            "limit": 4
        }
    },
    "data": [
        {
            "name": "INFINITY MICROFINANCE BANK",
            "code": "090157",
            "country": "nigeria",
            "currency": "NGN",
            "isEnabled": true,
            "type": "nuban",
            "createdAt": "2024-01-20T09:21:39.280Z",
            "updatedAt": "2024-01-20T09:21:39.280Z"
        },
        {
            "name": "Imo State MFB",
            "code": "090258",
            "country": "nigeria",
            "currency": "NGN",
            "isEnabled": true,
            "type": "nuban",
            "createdAt": "2024-01-20T09:21:39.280Z",
            "updatedAt": "2024-01-20T09:21:39.280Z"
        },
        {
            "name": "Imowo Microfinance Bank",
            "code": "090417",
            "country": "nigeria",
            "currency": "NGN",
            "isEnabled": true,
            "type": "nuban",
            "createdAt": "2024-01-20T09:21:39.280Z",
            "updatedAt": "2024-01-20T09:21:39.280Z"
        },
        {
            "name": "Ilora Microfinance Bank",
            "code": "090430",
            "country": "nigeria",
            "currency": "NGN",
            "isEnabled": true,
            "type": "nuban",
            "createdAt": "2024-01-20T09:21:39.280Z",
            "updatedAt": "2024-01-20T09:21:39.280Z"
        }
    ],
    "message": "successful",
    "status": 200
}
```
{% endcode %}
{% endtab %}
{% endtabs %}
