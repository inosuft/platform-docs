# List Mobile Networks

Get list of beneficiaries added to your Vacepay account.&#x20;

```
GET {{BASE_URL}}/resource/v1/networks
```

#### Optional Query Parameters

<table><thead><tr><th>Property</th><th width="158">Data Type</th><th width="279">Description</th><th>Example</th></tr></thead><tbody><tr><td>limit</td><td>string</td><td>Number of records per page</td><td>50</td></tr><tr><td>page</td><td>string</td><td>Page number to view</td><td>1</td></tr><tr><td>order</td><td>string</td><td>Arrangement of records in descending or ascending order</td><td>"asc" or "desc"</td></tr></tbody></table>

{% tabs %}
{% tab title="Node.js" %}
{% code lineNumbers="true" %}
```javascript
import Axios from 'axios';

// set the api url
const API_URL = `${BASE_URL}/resource/v1/networks`;

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
    "total": 4,
    "pagination": {},
    "data": [
        {
            "name": "MTN Nigeria",
            "description": "MTN Nigeria mobile network",
            "label": "mtn",
            "logo": "",
            "createdAt": "2023-12-28T17:29:53.658Z",
            "updatedAt": "2023-12-28T17:29:53.658Z",
            "slug": "mtn-nigeria"
        },
        {
            "name": "GLO Nigeria",
            "description": "Globacom Nigeria mobile network",
            "label": "glo",
            "logo": "",
            "createdAt": "2023-12-28T17:29:53.658Z",
            "updatedAt": "2023-12-28T17:29:53.658Z",
            "slug": "glo-nigeria"
        },
        {
            "name": "AIRTEL Nigeria",
            "description": "Airtel Nigeria mobile network",
            "label": "airtel",
            "logo": "",
            "createdAt": "2023-12-28T17:29:53.658Z",
            "updatedAt": "2023-12-28T17:29:53.658Z",
            "slug": "airtel-nigeria"
        },
        {
            "name": "9 Mobile Nigeria",
            "description": "9 Mobile Nigeria mobile network",
            "label": "9mobile",
            "logo": "",
            "createdAt": "2023-12-28T17:29:53.658Z",
            "updatedAt": "2023-12-28T17:29:53.658Z",
            "slug": "9-mobile-nigeria"
        }
    ],
    "message": "successfull",
    "status": 200
}
```
{% endcode %}
{% endtab %}
{% endtabs %}
