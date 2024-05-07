# List Countries

Get a list of your products on Vacepay.&#x20;

```
GET {{ BASE_URL }}/resource/v1/countries/list
```

#### Optional Query Parameters

<table><thead><tr><th>Property</th><th width="158">Data Type</th><th width="279">Description</th><th>Example</th></tr></thead><tbody><tr><td>limit</td><td>string</td><td>Number of records per page</td><td>50</td></tr><tr><td>page</td><td>string</td><td>Page number to view</td><td>1</td></tr><tr><td>order</td><td>string</td><td>Arrangement of records in descending or ascending order</td><td>"asc" or "desc"</td></tr></tbody></table>

{% tabs %}
{% tab title="Node.js" %}
{% code lineNumbers="true" %}
```javascript
import Axios from 'axios';

// set the api url
const API_URL = `${BASE_URL}/resource/v1/countries/list`;

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
    "count": 1,
    "total": 238,
    "pagination": {
        "next": {
            "page": 2,
            "limit": 1
        }
    },
    "data": [
        {
            "name": "Cyprus",
            "countryCode": "CY",
            "code3": "CYP",
            "capital": "Nicosia",
            "region": "Europe",
            "subregion": "Southern Europe",
            "currencyImage": "",
            "flag": "https://storage.googleapis.com/concreap-buckets/Cyprus_flag",
            "states": [
                {
                    "code": "04",
                    "name": "Ammochostos"
                },
                {
                    "code": "06",
                    "name": "Keryneia"
                },
                {
                    "code": "03",
                    "name": "Larnaka"
                },
                {
                    "code": "01",
                    "name": "Lefkosia"
                },
                {
                    "code": "02",
                    "name": "Lemesos"
                },
                {
                    "code": "05",
                    "name": "Pafos"
                }
            ],
            "timezones": [
                {
                    "name": "Asia/Famagusta",
                    "displayName": "Asia/Famagusta",
                    "label": "(UTC+02:00)Asia/Famagusta",
                    "countries": [
                        "CY"
                    ],
                    "utcOffset": 120,
                    "utcOffsetStr": "+02:00"
                },
                {
                    "name": "Asia/Nicosia",
                    "displayName": "Asia/Nicosia",
                    "label": "(UTC+02:00)Asia/Nicosia",
                    "countries": [
                        "CY"
                    ],
                    "utcOffset": 120,
                    "utcOffsetStr": "+02:00"
                }
            ],
            "createdAt": "2024-01-20T09:21:36.233Z",
            "updatedAt": "2024-01-20T09:21:36.233Z"
        }
    ],
    "message": "successful",
    "status": 200
}
```
{% endcode %}
{% endtab %}
{% endtabs %}
