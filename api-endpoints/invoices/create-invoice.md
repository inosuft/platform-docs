# Create Invoice

Create a new invoice on your Vacepay account.

```
POST {{ BASE_URL }}/vace/v1/corporate/invoice
```

#### Body Parameters

<table><thead><tr><th width="231">Property</th><th width="114">Data Type</th><th width="283">Description</th><th width="190">Example</th><th width="160">Required</th></tr></thead><tbody><tr><td>name</td><td>string</td><td>The name of the invoice.</td><td>"Quick Invoice"</td><td>Yes</td></tr><tr><td>number</td><td>string</td><td>The invoice number. Ensure this contain no spaces and special characters. <code>underscore</code> or <code>hyphen</code> can be used to separate characters</td><td>"QINK_00018"</td><td>Yes</td></tr><tr><td>dueAt</td><td>string</td><td>The invoice due date and time. Format is <code>yyyy/mm/dd hh:mm:ss</code> OR <code>yyyy-mm-dd hh:mm:ss</code> </td><td>"2024/01/28 00:30:45"</td><td>Yes</td></tr><tr><td>description</td><td>string</td><td>Invoice description</td><td>"New quick invoice"</td><td>No</td></tr><tr><td>recipient</td><td>object</td><td>An object that holds the invoice recipient's data and informaion.</td><td>N/A</td><td>Yes</td></tr><tr><td>recipient.type</td><td>string</td><td>Recipient type. This can be <code>individual</code> or <code>business</code>. Defaulted to <code>business</code></td><td>"business"</td><td>Yes</td></tr><tr><td>recipient.businessName</td><td>string</td><td>Recipient business name. This required only if recipient type is <code>business</code></td><td>"NANST Solutions"</td><td>Yes if type is business</td></tr><tr><td>recipient.firstName</td><td>string</td><td>Recipient first name</td><td>"Oluwatobi"</td><td>Yes</td></tr><tr><td>recipient.lastName</td><td>string</td><td>Recipient last name</td><td>"Immanuel"</td><td>Yes</td></tr><tr><td>recipient.email</td><td>string</td><td>Recipient email address</td><td>"hello@nanst.com"</td><td>Yes</td></tr><tr><td>recipient.phoneNumber</td><td>string</td><td>Recipient's 11-digit phone number</td><td>"08137031202"</td><td>Yes</td></tr><tr><td>recipient.phoneCode</td><td>string</td><td>Country phoneCode for the phoneNumber provided. Use the List Countries endpoint to get phoneCode.</td><td>"+234"</td><td>Yes</td></tr><tr><td>recipient.countryCode</td><td>string</td><td>Country code of the recipient's nationality. Use the List Countries endpoint to get <code>code2</code> of the country.</td><td>"NG"</td><td>Yes</td></tr><tr><td>recipient.address</td><td>string</td><td>Address of the recipient</td><td>"New NANST address"</td><td>Yes</td></tr><tr><td>recipient.city</td><td>string</td><td>City of the recipient</td><td>"Ikeja"</td><td>Yes</td></tr><tr><td>recipient.state</td><td>string</td><td>State of the recipient</td><td>"Lagos"</td><td>Yes</td></tr><tr><td>items</td><td>array[object]</td><td>An array of objects that holds the invoice items.</td><td>N/A</td><td>Yes</td></tr><tr><td>items.name</td><td>string</td><td>item name</td><td>"Brown D&#x26;G bag"</td><td>Yes</td></tr><tr><td>items.price</td><td>number</td><td>Item price</td><td>1500.99</td><td>Yes</td></tr><tr><td>items.quantity</td><td>number</td><td>Item quantity</td><td>2</td><td>Yes</td></tr><tr><td>vat</td><td>object</td><td>An object that holds the VAT data of the invoice</td><td>N/A</td><td>No</td></tr><tr><td>vat.title</td><td>string</td><td>VAT title</td><td>"Tax"</td><td>Yes</td></tr><tr><td>vat.type</td><td>string</td><td>VAT type. This can be <code>percentage</code> or <code>flat</code></td><td>"percentage"</td><td>Yes</td></tr><tr><td>vat.value</td><td>number</td><td>VAT value</td><td>5</td><td>Yes</td></tr><tr><td>partial</td><td>number</td><td>If specified, this indicates that a part of the total amount due has been paid already.</td><td>2000</td><td>No</td></tr><tr><td>isLink</td><td>boolean</td><td>This indicates if a payment link should be generated when the invoice is created</td><td>true</td><td>No</td></tr></tbody></table>

{% tabs %}
{% tab title="Node.js" %}
{% code lineNumbers="true" %}
```javascript
import Axios from 'axios';

// set the api url
const API_URL = `${BASE_URL}/vace/v1/corporate/invoice`;

// define request body
const data = {
    name: "NANST-INV",
    dueAt: "2024/01/28 00:30:45", 
    number: "NANST-00124", 
    description: "Invoice for nanst limited", 
    partial: 0,
    isLink: false,
    vat: {
        title: "TAX",
        type: "percentage",
        value: 5
    },
    recipient: {
        type: "business",
        businessName: "NANST Solutions Limited",
        firstName: "Oluwatobi",
        lastName: "Immanuel",
        email: "nanst@gmail.com",
        phoneNumber: "08137031202",
        phoneCode: "+234",
        countryCode: "NG",
        address: "Alausa, Ikeja Lagos.",
        city: "Ikeja",
        state: "Lagos"
    },
    items: [
        {
            name: "Brown D&G Bag",
            price: 2000.99,
            quantity: 2
        }
    ]
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
        "code": "VPIB3E319FB",
        "name": "NANST-INV",
        "number": "NANST-00124",
        "status": "pending",
        "link": "https://staging-web.vacepay.com/invoice/VPIB3E319FB",
        "VAT": {
            "title": "TAX",
            "type": "percentage",
            "value": 5
        },
        "summary": {
            "subtotal": 4001.98,
            "partialAmount": 0,
            "totalAmount": 4202.08
        },
        "description": "Invoice for nanst limited",
        "isEnabled": true,
        "inflow": {
            "value": 0,
            "count": 0
        },
        "items": [
            {
                "label": "ITMKFMFWS",
                "name": "Brown D&G Bag",
                "price": 2000.99,
                "quantity": 2,
                "total": 4001.98
            }
        ],
        "dueAt": {
            "date": "2024-01-28",
            "time": "00:30:45",
            "ISO": "2024-01-28T00:30:45.000Z"
        },
        "issuedAt": {
            "date": "2024-01-13",
            "time": "18:31:23",
            "ISO": "2024-01-13T18:31:23.094Z"
        },
        "paymentLink": "",
        "recipient": {
            "type": "business",
            "businessName": "NANST Solutions Limited",
            "firstName": "Oluwatobi",
            "lastName": "Immanuel",
            "email": "nanst@gmail.com",
            "phoneNumber": "08137031202",
            "phoneCode": "+234",
            "countryCode": "NG",
            "address": "Alausa, Ikeja Lagos.",
            "city": "Ikeja",
            "state": "Lagos"
        },
        "createdAt": "2024-01-13T18:31:23.061Z",
        "updatedAt": "2024-01-13T18:31:23.113Z"
    },
    "message": "successful",
    "status": 200
}
```
{% endcode %}
{% endtab %}
{% endtabs %}
