# Fetch Payment Link

Get a single product on your Vacepay account

```
GET {{ BASE_URL }}/vace/v1/corporate/payment/{{slug}}
```

#### Url Parameters

<table><thead><tr><th width="129">Property</th><th>Data Type</th><th width="277">Description</th><th width="200">Example</th><th>Required</th></tr></thead><tbody><tr><td>slug</td><td>string</td><td>The payment link slug</td><td>"crowd-fund"</td><td>Yes</td></tr><tr><td></td><td></td><td></td><td></td><td></td></tr></tbody></table>

{% tabs %}
{% tab title="Node.js" %}
{% code lineNumbers="true" %}
```javascript
import Axios from 'axios';

// set the api url
const API_URL = `${BASE_URL}/vace/v1/corporate/payment/${slug}`;

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
        "name": "Crowd Fund School",
        "slug": "crowd-fund",
        "link": "https://staging-web.vacepay.com/link/crowd-fund",
        "qrcode": "https://storage.googleapis.com/concreap-buckets/qrcode-4ebc1b81",
        "redirectUrl": "",
        "feature": "request",
        "type": "fixed",
        "isEnabled": true,
        "message": "Thank you for your payment",
        "description": "",
        "amount": 5000,
        "totalAmount": 15000,
        "createdAt": "2024-01-13T05:39:48.624Z",
        "updatedAt": "2024-01-13T06:12:53.060Z",
        "options": {
            "card": true,
            "transfer": true,
            "bank": false,
            "ussd": false,
            "bankQR": false
        }
    },
    "message": "successful",
    "status": 200
}
```
{% endcode %}
{% endtab %}
{% endtabs %}
