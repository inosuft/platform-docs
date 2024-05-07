# Remove Invoice Item

Update invoice on your Vacepay account. Remove and adjust an invoice item

```
PUT {{ BASE_URL }}/vace/v1/corporate/remove-invoice-item/{{code}}
```

#### Body Parameters

<table><thead><tr><th width="231">Property</th><th width="114">Data Type</th><th width="283">Description</th><th width="190">Example</th><th width="149">Required</th></tr></thead><tbody><tr><td>label</td><td>string</td><td>The label of the item to be removed</td><td>VPIFFEE52E2</td><td>Yes</td></tr></tbody></table>

{% tabs %}
{% tab title="Node.js" %}
{% code lineNumbers="true" %}
```javascript
import Axios from 'axios';

// set the api url
const API_URL = `${BASE_URL}/vace/v1/corporate/remove-invoice-item/${code}`;

// define request body
const data = {
    label: "VPIFFEE52E2",
}

// make request using axios
Axios({
    method: "PUT",
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
    "data": {
        "items": [
            {
                "label": "ITMKFMFWS",
                "name": "Brown D&G Bag",
                "price": 2000.99,
                "quantity": 2,
                "total": 4001.98
            }
        ],
        "summary": {
            "subtotal": 4001.98,
            "partialAmount": 0,
            "totalAmount": 4202.08
        }
    },
    "message": "successful",
    "status": 200
}
```
{% endcode %}
{% endtab %}
{% endtabs %}
