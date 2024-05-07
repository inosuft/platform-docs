# Create Product

Create a new product on your Vacepay account.

```
POST {{ BASE_URL }}/vace/v1/corporate/product
```

#### Body Parameters

<table><thead><tr><th width="135">Property</th><th width="114">Data Type</th><th width="283">Description</th><th width="190">Example</th><th>Required</th></tr></thead><tbody><tr><td>name</td><td>string</td><td>The name of the product</td><td>"Laptop Bag"</td><td>Yes</td></tr><tr><td>avatar</td><td>base64 string</td><td>The base64 string value of the product image. Recommended size is 5MB.</td><td>"base64..."</td><td>No</td></tr><tr><td>code</td><td>string</td><td>Your preferred product code</td><td>"MYPRODUCTXD"</td><td>No</td></tr><tr><td>description</td><td>string</td><td>The product description</td><td>"This is a new product"</td><td>No</td></tr><tr><td>price</td><td>number</td><td>The price of the product. This must be in 2 decimal places only.</td><td>4500.99</td><td>Yes</td></tr><tr><td>isLink</td><td>boolean</td><td>This helps you specify if you want a payment link be generated automatically for the product. This is defaulted to <code>false</code></td><td>true</td><td>No</td></tr></tbody></table>

{% hint style="info" %}
Please note that the prefix "VPD" will be added to every product code you provide.
{% endhint %}

{% tabs %}
{% tab title="Node.js" %}
{% code lineNumbers="true" %}
```javascript
import Axios from 'axios';

// set the api url
const API_URL = `${BASE_URL}/vace/v1/corporate/product`;

// define request body
const base64_image = "base64...";
const data = {
    "name": "Plastic Modern Chair",  
    "avatar": `${base64_image}`, 
    "code": "VPDMYPROPLASTXD", 
    "description": "This is the new plastic product", 
    "price": 3500.99,
    "isLink": true
}

// make request using axios
Axios({
    method: "GET",
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
        "avatar": "",
        "code": "VPDMYPROPLASTXD",
        "description": "This is a new platsic product",
        "isEnabled": true,
        "name": "Plastic Modern Chair",
        "price": 3500.99,
        "slug": "plastic-modern-chair",
        "inflow": {
            "value": 0,
            "count": 0
        },
        "createdAt": "2024-01-10T13:43:06.899Z",
        "updatedAt": "2024-01-10T13:43:07.398Z",
        "paymentLink": "https://staging-web.vacepay.com/link/vpdmyproplastxd"
    },
    "message": "successful",
    "status": 200
}
```
{% endcode %}
{% endtab %}
{% endtabs %}
