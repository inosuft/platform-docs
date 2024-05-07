# Update Payment Link

Update an existing payment link on your Vacepay account.

```
PUT {{ BASE_URL }}/vace/v1/corporate/payment/{{slug}}
```

#### Body Parameters

<table><thead><tr><th width="135">Property</th><th width="114">Data Type</th><th width="283">Description</th><th width="210">Example</th><th width="167">Required</th></tr></thead><tbody><tr><td>name</td><td>string</td><td>The name of the payment link</td><td>"Donation Request"</td><td>No</td></tr><tr><td>feature</td><td>string</td><td>The feature type of the payment link. This can either be <code>request</code>, <code>product</code> or <code>invoice</code></td><td>"request"</td><td>No</td></tr><tr><td>type</td><td>string</td><td>Specifies the amount type of the payment link. Can be <code>fixed</code> or <code>dynamic</code></td><td>"fixed"</td><td>No</td></tr><tr><td>amount</td><td>number</td><td>Amount of required for the payment link. This should be set if type is fixed</td><td>1000.99</td><td>Only if type is fixed</td></tr><tr><td>redirectUrl</td><td>string</td><td>Preferred payment link redirect url. Customers will be redirected to this link on payment success or failure.</td><td>""</td><td>No</td></tr><tr><td>message</td><td>string</td><td>Success message after a successful payment.</td><td>"Thank you for your payment"</td><td>No</td></tr><tr><td>slug</td><td>string</td><td>Customize your payment link url with the payment link slug. This should be unique and does not accept spaces or special characters</td><td>"donation-request"</td><td>No</td></tr><tr><td>description</td><td>string</td><td>Describe the payment link and its purpose.</td><td>"For donation"</td><td>No</td></tr><tr><td>splits</td><td>array</td><td>An array of strings that holds subaccount codes if you plan to split the payment.</td><td>[ "VSA_6yhyzzkcHc" ]</td><td>No</td></tr></tbody></table>

{% tabs %}
{% tab title="Node.js" %}
{% code lineNumbers="true" %}
```javascript
import Axios from 'axios';

// set the api url
const API_URL = `${BASE_URL}/vace/v1/corporate/payment/${slug}`;

// define request body
const data = {
  name: "",
  feature: "",
  type: "fixed",
  amount: 1500.00,
  redirectUrl: "",
  message: "Thank you for your payment",
  slug: "",
  description: "",
  splits: []
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
    "data": {
        "name": "Donation Request",
        "slug": "donation-request",
        "link": "https://staging-web.vacepay.com/link/donation-request",
        "qrcode": "https://storage.googleapis.com/concreap-buckets/qrcode-fb85107d",
        "redirectUrl": "",
        "feature": "product",
        "type": "fixed",
        "isEnabled": false,
        "message": "Thank you for your payment",
        "description": "Request link for church donation",
        "amount": 1500,
        "totalAmount": 0,
        "createdAt": "2024-01-20T08:39:25.842Z",
        "updatedAt": "2024-01-20T08:42:22.199Z",
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
