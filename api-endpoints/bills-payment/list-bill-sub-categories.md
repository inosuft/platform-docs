# List Bill Sub-Categories

Get a list of bill subcategories from a bill category Vacepay supports

```
POST {{BASE_URL}}/vace/v1/corporate/bill-sub-categories
```

#### Body Parameters

<table><thead><tr><th width="136">Property</th><th width="158">Data Type</th><th width="279">Description</th><th>Example</th><th>Required</th></tr></thead><tbody><tr><td>categoryId</td><td>string or number</td><td>The bill category id</td><td>4</td><td>Yes</td></tr></tbody></table>

{% tabs %}
{% tab title="Node.js" %}
{% code lineNumbers="true" %}
```javascript
import Axios from 'axios';

// set the api url
const API_URL = `${BASE_URL}/vace/v1/corporate/bill-sub-categories`;

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
    "data": [
        {
            "label": "cable",
            "category": {
                "categoryId": 4,
                "name": "Cable TV Subscription",
                "subCategory": "GOTv (MultiChoice) Subscription Payment",
                "mainCategory": ""
            },
            "validation": {
                "customer": true,
                "amount": true,
                "hasBillerDetails": true,
                "select": false
            },
            "billerId": "1465",
            "billerItem": {
                "name": "GOtv Max -#4150",
                "itemId": 1465,
                "amount": "4150.00"
            },
            "countryCode": "NG",
            "currency": "NGN",
            "itemId": 1465
        },
        {
            "label": "cable",
            "category": {
                "categoryId": 4,
                "name": "Cable TV Subscription",
                "subCategory": "GOTv (MultiChoice) Subscription Payment",
                "mainCategory": ""
            },
            "validation": {
                "customer": true,
                "amount": true,
                "hasBillerDetails": true,
                "select": false
            },
            "billerId": "1466",
            "billerItem": {
                "name": "GOtv Jolli Bouquet -#2800",
                "itemId": 1466,
                "amount": "2800.00"
            },
            "countryCode": "NG",
            "currency": "NGN",
            "itemId": 1466
        }
    ],
    "message": "successful",
    "status": 200
}
```
{% endcode %}
{% endtab %}
{% endtabs %}
