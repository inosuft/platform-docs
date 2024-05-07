# Fetch Product

Get a single product on your Vacepay account

```
GET {{ BASE_URL }}/vace/v1/corporate/product/{code}
```

#### Url Parameters

<table><thead><tr><th width="129">Property</th><th>Data Type</th><th width="277">Description</th><th width="200">Example</th><th>Required</th></tr></thead><tbody><tr><td>code</td><td>string</td><td>The product code</td><td>"VPDMYPROPLASTXD"</td><td>Yes</td></tr><tr><td></td><td></td><td></td><td></td><td></td></tr></tbody></table>

{% tabs %}
{% tab title="Node.js" %}
{% code lineNumbers="true" %}
```javascript
import Axios from 'axios';

// set the api url
const API_URL = `${BASE_URL}/vace/v1/corporate/product/${code}`;

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
        "avatar": "",
        "code": "VPDMYPROPLASTXD",
        "description": "This is a new platsic product",
        "isEnabled": true,
        "name": "Plastic Chair",
        "price": 5000,
        "slug": "plastic-chair",
        "inflow": {
            "value": 0,
            "count": 0
        },
        "createdAt": "2024-01-10T13:43:06.899Z",
        "updatedAt": "2024-01-10T13:52:01.552Z"
    },
    "message": "successful",
    "status": 200
}
```
{% endcode %}
{% endtab %}
{% endtabs %}
