# Attach Payment Resource

Update an existing payment link on your Vacepay account.

```
PUT {{ BASE_URL }}/vace/v1/corporate/payment-resource/{{slug}}
```

{% hint style="info" %}
You can only attach a resource ( i.e. product or invoice ) to a payment link if the feature of the payment link is `product` or `invoice`&#x20;
{% endhint %}

#### Body Parameters

<table><thead><tr><th width="135">Property</th><th width="114">Data Type</th><th width="283">Description</th><th width="210">Example</th><th width="167">Required</th></tr></thead><tbody><tr><td>type</td><td>string</td><td>The type of resource to attach. This can be <code>product</code> or <code>invoice</code></td><td>"product"</td><td>Yes</td></tr><tr><td>code</td><td>string</td><td>The code of the resource to attach. This can be the product code or the invoice code</td><td>"VPDLASTXD"</td><td>Yes</td></tr></tbody></table>

{% tabs %}
{% tab title="Node.js" %}
{% code lineNumbers="true" %}
```javascript
import Axios from 'axios';

// set the api url
const API_URL = `${BASE_URL}/vace/v1/corporate/payment-resource/${slug}`;

// define request body
const data = {
  type: "product",
  code: "VPDLASTXD"
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
        "amount": 3500.99,
        "totalAmount": 0,
        "createdAt": "2024-01-20T08:39:25.842Z",
        "updatedAt": "2024-01-20T08:57:32.676Z",
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

{% hint style="info" %}
Please note that the amount of the resource ( Product or Invoice ) you attach to a payment link overrides the default amount ( if already set ) of the payment link.
{% endhint %}
