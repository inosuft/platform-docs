# 🫓 Status & Responses

This explains the payload response and statuses returned by our API endpoints. These are commonly seen when consuming our endpoints. Note, these applies mostly on every endpoint.

#### General Response Structure

```javascript
{
    "error": false,
    "errors": [],
    "data": {},
    "message": "",
    "status": 200
}
```

The response data structure is exactly the same for every response on our API call. Find the description below

<table><thead><tr><th width="119">Property</th><th width="168">Data Type</th><th width="353">Description</th><th>Example</th></tr></thead><tbody><tr><td>error</td><td>boolean</td><td>Indicates if there is an error on the response or not. This can either be <code>true</code> or <code>false</code></td><td>false</td></tr><tr><td>errors</td><td>array of strings</td><td>This array contains strings of error descriptions if <code>error</code> above is true</td><td>["error"]</td></tr><tr><td>data</td><td>object or array</td><td>This contains response data as an object or an array</td><td>{ name: "to" }</td></tr><tr><td>message</td><td>string</td><td>The response message</td><td>"successful"</td></tr><tr><td>status</td><td>number</td><td>The response status code</td><td>200</td></tr></tbody></table>

#### Pagination Data response

When API requests are made to retrieve a list of data ( ex. a list of banks ), the response comes with pagination information that can help you navigate the list. Below is an example of a response when a list of banks is requested.

```javascript
{
    "error": false,
    "errors": [],
    "count": 1,
    "total": 533,
    "pagination": {
        "next": {
            "page": 3,
            "limit": 1
        },
        "prev": {
            "page": 1,
            "limit": 1
        }
    },
    "data": [
        {
            "name": "Polaris Bank",
            "code": "076",
            "country": "nigeria",
            "currency": "NGN",
            "isEnabled": true,
            "type": "nuban",
            "createdAt": "2024-01-20T09:21:39.261Z",
            "updatedAt": "2024-01-20T09:21:39.261Z"
        }
    ],
    "message": "successful",
    "status": 200
}
```

{% hint style="info" %}
**More about Pagination**\
\
Read more about how to navigate lists with Vacepay pagination here
{% endhint %}

#### Transaction Status Descriptions

<table><thead><tr><th width="221">Status</th><th width="376">Description</th><th width="380">Recommended Action</th></tr></thead><tbody><tr><td>pending</td><td>Transaction is in progress and pending completion</td><td>You can query the <a href="https://vace-docs.gitbook.io/corporate/api-endpoints/transactions/verify-transaction">verify transaction endpoint</a> to check the status of the transaction.</td></tr><tr><td>processing</td><td>A partial payment has been made on the transaction</td><td>You can query the <a href="https://vace-docs.gitbook.io/corporate/api-endpoints/transactions/verify-transaction">verify transaction endpoint</a> or wait till the transaction is completed.</td></tr><tr><td>successful / completed</td><td>Transaction has been processed successfully</td><td>Mark transaction as successful on your end</td></tr><tr><td>refunded</td><td>The transaction value has been refunded. This is usually linked to another transaction that tracks if the refund is successful.</td><td>Mark transaction as refunded and check the linked transaction to know the status of the refund.</td></tr><tr><td>cancelled</td><td>Transaction was cancelled. This means transaction was not processed at all.</td><td>Mark transaction as cancelled on your end.</td></tr><tr><td>failed</td><td>Transaction was processed but failed.</td><td>Mark transaction as failed. Initiate a refund or reach out to us as the case may be.</td></tr></tbody></table>

#### Transaction Feature Descriptions

<table><thead><tr><th width="278">Feature</th><th>Description</th></tr></thead><tbody><tr><td>bank-account</td><td>This indicates that your wallet was funded via your Vacepay virtual account number.</td></tr><tr><td>wallet-transfer</td><td>This means you send money from your wallet to a Vacepay user or an NGN bank account</td></tr><tr><td>wallet-withdraw</td><td>This means you withdraw money from your wallet to your NGN bank account</td></tr><tr><td>wallet-airtime</td><td>This means you bought airtime via your Vacepay wallet</td></tr><tr><td>wallet-data</td><td>This means your purchased data using via your Vacepay wallet</td></tr><tr><td>wallet-bill</td><td>This means you made a bill payment via your Vacepay wallet</td></tr><tr><td>wallet-refund</td><td>This means you initiated a refund to an NGN bank account and indicated that the refund be via your Vacepay wallet.</td></tr><tr><td>api-refund</td><td>This means you initiated a refund and specified that you want Vacepay to handle the refund on your behalf.</td></tr><tr><td>wallet-chargeback</td><td>This transaction is a chargeback initiated by Vacepay on your account on Vacepay.</td></tr><tr><td>payment-link</td><td>This is a transaction created via any payment link on your Vacepay account.</td></tr><tr><td>internal-credit</td><td>This transaction is created on your account because another Vacepay user sends money to your Vacepay wallet.</td></tr><tr><td>internal-debit</td><td>This transaction is created when you send money to another Vacepay user via their phone number.</td></tr></tbody></table>

#### Invoice Status Description

<table><thead><tr><th width="151">Status</th><th width="350">Description</th><th>Recommended Action</th></tr></thead><tbody><tr><td>pending</td><td>The invoice was just created and has not been paid for.</td><td>Copy and share the invoice link with your customer/client</td></tr><tr><td>paid</td><td>The invoice has been paid for and no payment can be made on the invoice again</td><td>Mark invoice as paid</td></tr><tr><td>overdue</td><td>The due date on invoice has passed</td><td>Mark invoice as overdue and send a reminder to your customer/client.</td></tr><tr><td>failed</td><td>The payment attempt on the invoice failed. Another payment can be made at this point</td><td>inform your client to try and make a payment again.</td></tr></tbody></table>
