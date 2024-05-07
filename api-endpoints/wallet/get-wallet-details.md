# Get Wallet Details

This endpoint helps you get the details of your Vacepay Corporate account details.

```
GET {{ BASE_URL }}/vace/v1/corporate/wallet
```

{% tabs %}
{% tab title="Node.js" %}
{% code lineNumbers="true" %}
```javascript
import Axios from 'axios';

// set the api url
const API_URL = `${BASE_URL}/vace/v1/corporate/wallet`;

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
        "walletID": "VPW5ca28d98-319d4dc7",
        "balance": {
            "settlement": 0,
            "available": 27100,
            "locked": 0
        },
        "currency": "NGN",
        "createdAt": "2023-12-28T17:33:30.131Z",
        "updatedAt": "2024-01-02T10:05:11.121Z",
        "analytics": {
            "inflow": {
                "value": 50001.97,
                "count": 3,
                "updatedAt": "2023-12-31T09:55:52.194Z"
            },
            "outflow": {
                "value": 4750,
                "count": 3,
                "updatedAt": "2023-12-31T14:16:17.317Z"
            },
            "transfer": {
                "value": 6150,
                "count": 2,
                "updatedAt": "2024-01-02T10:05:11.120Z"
            },
            "withdrawal": {
                "value": 2000,
                "count": 1,
                "updatedAt": "2023-12-31T14:00:06.022Z"
            }
        }
    },
    "message": "successful",
    "status": 200
}
```
{% endcode %}
{% endtab %}
{% endtabs %}
