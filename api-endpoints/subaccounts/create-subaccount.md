# Create Subaccount

Create a new subaccount on your Vacepay account.

```
POST {{ BASE_URL }}/vace/v1/corporate/subaccount
```

#### Body Parameters

<table><thead><tr><th width="135">Property</th><th width="114">Data Type</th><th width="283">Description</th><th width="190">Example</th><th>Required</th></tr></thead><tbody><tr><td>name</td><td>string</td><td>The name of the subaccount</td><td>"Corporate NATS"</td><td>Yes</td></tr><tr><td>description</td><td>string</td><td>Your description for the subaccount</td><td>"This is a business partner"</td><td>No</td></tr><tr><td>accountNo</td><td>string</td><td>The recipient bank account number to settle money to.</td><td>"0125318431"</td><td>Yes</td></tr><tr><td>bankCode</td><td>string</td><td>The bank sort code for the account number provided. Use the List Banks endpoint.</td><td>"035"</td><td>Yes</td></tr><tr><td>email</td><td>string</td><td>The contact email for the subaccount</td><td>"hello@corporatenats.com"</td><td>Yes</td></tr><tr><td>phoneNumber</td><td>string</td><td>The 11-digit phone number for the subaccount</td><td>"08137031202"</td><td>Yes</td></tr><tr><td>phoneCode</td><td>string</td><td>The dial country code for the phone number provided. Defaulted to "+234"</td><td>"+234"</td><td>Yes</td></tr><tr><td>split</td><td>object</td><td>The defined object to hold payment split data.</td><td>N/A</td><td>Yes</td></tr><tr><td>split.type</td><td>string</td><td>Type of split. This can either be <code>percentage</code> or <code>flat</code></td><td>"percentage"</td><td>Yes</td></tr><tr><td>split.value</td><td>number</td><td>The value of the split. For <code>percentage</code>, range is between 1 - 100 and it cannot be more than 100. </td><td>10.05</td><td>Yes</td></tr></tbody></table>

{% tabs %}
{% tab title="Node.js" %}
{% code lineNumbers="true" %}
```javascript
import Axios from 'axios';

// set the api url
const API_URL = `${BASE_URL}/vace/v1/corporate/subaccount`;

// define request body
const data = {
    name: "Corporate NATS", 
    description: "Corporate NATS subaccount for vacepay", 
    accountNo: "0125318431", 
    bankCode: "035", 
    email: "hello@corporatenats.com", 
    phoneCode: "+234", 
    phoneNumber: "08137031202", 
    split: {
        type: "percentage",
        value: 10.05
    }
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
        "code": "VSA_6yhyzzkcHc",
        "isEnabled": true,
        "name": "Corporate NATS",
        "description": "Corporate NATS subaccount for vacepay",
        "phoneNumber": "08137031202",
        "phoneCode": "+234",
        "email": "hello@corportenats.com",
        "inflow": {
            "value": 0,
            "count": 0
        },
        "split": {
            "value": 10.05,
            "type": "percentage"
        },
        "bank": {
            "accountNo": "0125318431",
            "accountName": "CONCREAP TECHNOLOGY SOLUTIONS LIMITED",
            "bankCode": "035",
            "legalName": "Wema Bank",
            "name": "wema bank"
        }
        "slug": "corporate-nats",
        "createdAt": "2024-01-12T03:00:09.675Z",
        "updatedAt": "2024-01-12T03:00:09.675Z",
    },
    "message": "successful",
    "status": 200
}
```
{% endcode %}
{% endtab %}
{% endtabs %}
