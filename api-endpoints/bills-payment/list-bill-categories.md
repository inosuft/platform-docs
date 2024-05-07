# List Bill Categories

Get a list of bill categories supported by Vacepay.

```
GET {{BASE_URL}}/vace/v1/corporate/bill-categories
```



{% tabs %}
{% tab title="Node.js" %}
{% code lineNumbers="true" %}
```javascript
import Axios from 'axios';

// set the api url
const API_URL = `${BASE_URL}/vace/v1/corporate/bill-categories`;

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
    "data": [
        {
            "category": {
                "categoryId": 4,
                "name": "Cable TV Subscription",
                "subCategory": "",
                "mainCategory": ""
            },
            "label": "cable",
            "countryCode": "NG"
        },
        {
            "category": {
                "categoryId": 6,
                "name": "Power / Electricity Payments",
                "subCategory": "",
                "mainCategory": ""
            },
            "label": "utility",
            "countryCode": "NG"
        },
        {
            "category": {
                "categoryId": 15,
                "name": "Betting",
                "subCategory": "",
                "mainCategory": ""
            },
            "label": "utility",
            "countryCode": "NG"
        }
    ],
    "message": "successful",
    "status": 200
}
```
{% endcode %}
{% endtab %}
{% endtabs %}
