# Remove Subaccount

Remove subaccount on an existing payment link

```
PUT {{ BASE_URL }}/vace/v1/corporate/remove-subaccount/{{slug}}
```

#### Body Parameters

<table><thead><tr><th width="135">Property</th><th width="114">Data Type</th><th width="283">Description</th><th width="210">Example</th><th width="167">Required</th></tr></thead><tbody><tr><td>code</td><td>string</td><td>The subaccount code to be removed</td><td>"vpd648394tc"</td><td>Yes</td></tr></tbody></table>

{% tabs %}
{% tab title="Node.js" %}
{% code lineNumbers="true" %}
```javascript
import Axios from 'axios';

// set the api url
const API_URL = `${BASE_URL}/vace/v1/corporate/remove-subaccount/${slug}`;

// define request body
const data = {
  code: "vpd648394tc"
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
        "slug": "donation-request",
        "link": "https://staging-web.vacepay.com/link/donation-request",
        "qrcode": "https://storage.googleapis.com/concreap-buckets/qrcode-fb85107d"
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
