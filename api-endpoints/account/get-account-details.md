# Get Account Details

This endpoint helps you get the details of your Vacepay Corporate account details.

```
GET {{BASE_URL}}/vace/v1/corporate/account
```

{% tabs %}
{% tab title="Node.js" %}
{% code lineNumbers="true" %}
```javascript
import Axios from 'axios';

// set the api url
const API_URL = `${BASE_URL}/vace/v1/corporate/account`;

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
    "data": {
        "tier": "3",
        "dailyTransaction": {
            "label": "3M",
            "limit": 300000000
        },
        "name": "Softklin Services",
        "email": "softklinservices@gmail.com",
        "phoneNumber": "+2348137031202",
        "officialEmail": "softklinservices@gmail.com",
        "profile": "Hello Softklin Services",
        "staffStrength": "10",
        "industry": "Fintech",
        "category": "Financial Technology",
        "logo": "",
        "cover": "",
        "socials": [
            {
                "name": "facebook",
                "url": "@softklin",
                "username": "@softklin"
            },
            {
                "name": "twitter",
                "url": "@softklin",
                "username": "@softklin"
            },
            {
                "name": "instagram",
                "url": "@softklin",
                "username": "@softklin"
            },
            {
                "name": "threads",
                "url": "@softklin",
                "username": "@softklin"
            },
            {
                "name": "linkedin",
                "url": null,
                "username": "business"
            }
        ],
        "country": {
            "name": "Nigeria",
            "code": "NG",
            "phoneCode": "+234"
        },
        "location": {
            "address": "Alausa, Ikeja Lagos",
            "city": "Ikeja",
            "postalCode": "120001",
            "state": "lagos"
        },
        "bank": {
            "accountNo": "0252872742",
            "accountName": "AGBELEYE OLUWATOBI EMMANUEL",
            "name": "Guaranty Trust Bank",
            "bankCode": "058",
            "updatedAt": "2024-01-09T07:43:40.110+00:00"
        }
    },
    "message": "successful",
    "status": 200
}
```
{% endcode %}
{% endtab %}
{% endtabs %}
