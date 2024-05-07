# Filter Products

Get a list of your products on Vacepay.&#x20;

```
POST {{ BASE_URL }}/vace/v1/corporate/filter-products
```

#### Optional Query Parameters

<table><thead><tr><th>Property</th><th width="158">Data Type</th><th width="279">Description</th><th>Example</th></tr></thead><tbody><tr><td>limit</td><td>string</td><td>Number of records per page</td><td>50</td></tr><tr><td>page</td><td>string</td><td>Page number to view</td><td>1</td></tr><tr><td>order</td><td>string</td><td>Arrangement of records in descending or ascending order</td><td>"asc" or "desc"</td></tr></tbody></table>

#### Body Parameters

<table><thead><tr><th width="135">Property</th><th width="158">Data Type</th><th width="283">Description</th><th width="107">Example</th><th>Required</th></tr></thead><tbody><tr><td>isEnabled</td><td>boolean</td><td>Specify filter value for the enabled status of the product</td><td>true</td><td>Yes, if no other property is specified</td></tr><tr><td></td><td></td><td></td><td></td><td></td></tr></tbody></table>

{% tabs %}
{% tab title="Node.js" %}
{% code lineNumbers="true" %}
```javascript
import Axios from 'axios';

// set the api url
const API_URL = `${BASE_URL}/vace/v1/corporate/filter-products`;

// define request body
const data = {
    isEnabled: true
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
    "count": 3,
    "total": 3,
    "pagination": {},
    "data": [
        {
            "avatar": "",
            "code": "VPDMYPRODUCTXD",
            "description": "This split is for sending money to my settlement accounts",
            "isEnabled": true,
            "name": "Black Shirt",
            "price": 3500.99,
            "slug": "black-shirt",
            "inflow": {
                "value": 0,
                "count": 0
            },
            "createdAt": "2023-12-31T21:23:27.440Z",
            "updatedAt": "2023-12-31T21:26:12.328Z"
        },
        {
            "avatar": "https://storage.googleapis.com/concreap-buckets/product-vpdextq1knp-avatar",
            "code": "VPDexTq1knp",
            "description": "Homemade soup for families",
            "isEnabled": true,
            "name": "Homemade Soup",
            "price": 5000.99,
            "slug": "homemade-soup",
            "inflow": {
                "value": 10001.98,
                "count": 2
            },
            "createdAt": "2023-12-30T07:46:26.915Z",
            "updatedAt": "2023-12-30T14:26:14.628Z"
        },
        {
            "avatar": "https://storage.googleapis.com/concreap-buckets/product-vpdd&gfr54bva1-avatar",
            "code": "VPDD&GfR54BVA1",
            "description": "This is a D&G Brown Bag to sell",
            "isEnabled": true,
            "name": "D&G Brown Bag",
            "price": 4500.99,
            "slug": "dandg-brown-bag",
            "inflow": {
                "value": 0,
                "count": 0
            },
            "createdAt": "2023-12-30T05:47:44.160Z",
            "updatedAt": "2023-12-30T06:01:31.138Z"
        }
    ],
    "message": "successful",
    "status": 200
}
```
{% endcode %}
{% endtab %}
{% endtabs %}
