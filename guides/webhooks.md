# 🧀 Webhooks

Webhooks provide a way to receive notifications from Vacepay for your transactions and API calls in real time. While your transaction is being processed, its status progresses until it is completed. This makes it very important to get the final status for that transaction, and that's where webhooks are very beneficial.

Described easily, a webhook URL is a "POST" request endpoint on your server that can receive API requests from Vacepay platform. Note that the request is going to be an **HTTP POST request**.

{% hint style="info" %}
💡**Helpful Tip**\
\
We recommend that you use webhook to provide value to your customers over using callbacks or polling. With callbacks, we don't have control over what happens on the customer's end and neither do you.
{% endhint %}

### Events and notification types you can receive

* Successful completion of a "Pay-In" transaction
* Successful completion of a "Pay-Out" transaction
* Successful completion of a "VAS" transaction
* Receive notifications on your payment links when transactions are successful

When your webhook URL receives an event, it needs to parse and acknowledge the event. Acknowledging an event means returning a `200 OK` in the HTTP header. Without a `200 OK` in the response header, we’ll keep sending events for 24 hours.

{% hint style="info" %}
Please note that you will receive notifications too when transactions fail based of events. Each event type will be specified and data structured properly for you.
{% endhint %}

### Setting up your Webhook URL

You can specify your webhook URL in the [<mark style="color:orange;">Webhook & API Key</mark>](#user-content-fn-1)[^1] page, a sub-page under the Settings page of your dashboard. Make sure that the webhook URL is unauthenticated and publicly available.

The request to the webhook URL comes with a payload, and this payload contains the details of the transaction for which you are being notified.\


<figure><img src="../.gitbook/assets/Screenshot 2024-01-07 at 5.38.40 PM.png" alt=""><figcaption><p>Setup your webhook URL here</p></figcaption></figure>

{% hint style="info" %}
Your webhook URL must return any of the standard HTTP success status codes the first time you are setting it up on your dashboard.
{% endhint %}

### Verify webhook events origin

Since your webhook URL is publicly available, you need to verify that events originate from Vacepay and not a bad actor. To verify event orgin from Vacepay, use the signature validation method.\
\
Events sent from Vacepay carry the `x-vacepay-signature header`. The value of this header is a `HMAC SHA512` signature of the event payload signed using your API key. Verifying the header signature should be done before processing the event payload.

{% tabs %}
{% tab title="Node.js" %}
```typescript
import crypto from 'crypto';
const API_KEY = process.env.VACEPAY_API_KEY;

// Using Express
app.post("/my/webhook/url", function(req, res, next) {
    
    const payload = req.body;
    const datastring = JSON.stringify(payload);
    const signature = req.headers['x-vacepay-signature'];

    const hash = crypto
    .createHmac('sha512', `${API_KEY}`)
    .update(datastring)
    .digest('hex');

    if(hash === signature){
    
        // process payloand
        console.log(payload)
    
    }
    
    res.send(200);
});

```
{% endtab %}

{% tab title="Second Tab" %}

{% endtab %}
{% endtabs %}

### Webhook go live checklist

* Add your webhook URL on your [Vacepay dashboard](https://pilot.vacepay.com)
* Ensure your webhook URL is publicly available (localhost URLs cannot receive events)
* If using .htaccess kindly remember to add the trailing / to the URL
* Test your webhook to ensure you’re getting the JSON body and returning a 200 OK HTTP response
* If your webhook function has long-running tasks, you should first acknowledge receiving the webhook by returning a 200 OK before proceeding with the long-running tasks
* If we don’t get a 200 OK HTTP response from your webhooks, we will flag it as a failed attempt
* Failed attempts are retried every 1 minute for the first 3 tries, then we switch to sending hourly for the next 24 hours

### Supported webhook events

{% tabs %}
{% tab title="payin.success" %}
```javascript
// Some code
```
{% endtab %}

{% tab title="payin.failed" %}

{% endtab %}

{% tab title="payin.link.success" %}

{% endtab %}

{% tab title="payin.link.failed" %}

{% endtab %}

{% tab title="payout.success" %}

{% endtab %}

{% tab title="payout.failed" %}

{% endtab %}

{% tab title="vas.success" %}

{% endtab %}

{% tab title="vas.failed" %}

{% endtab %}

{% tab title="more" %}

{% endtab %}
{% endtabs %}

### Types of webhook events

<table><thead><tr><th width="226">Event Type</th><th>Description</th></tr></thead><tbody><tr><td>payin.success</td><td>Your wallet was funded via your virtual account number</td></tr><tr><td>payin.failed</td><td>Funding on your wallet, via your virtual account numbr failed</td></tr><tr><td>payin.link.success</td><td>A payment was made using one of your active payment links</td></tr><tr><td>payin.link.failed</td><td>Payment via your payment link failed</td></tr><tr><td>payout.success</td><td>Withdrawal or transfer transaction from your wallet was successful</td></tr><tr><td>payout.failed</td><td>Withdrawal or transfer from wallet failed</td></tr><tr><td>vas.success</td><td>A VAS transaction on your wallet was successful. E.g. buy airtime</td></tr><tr><td>vas.failed</td><td>A VAS transaction (e.g. pay bill) on your account failed</td></tr><tr><td>refund.success</td><td>Initiated refund on your account was successful</td></tr><tr><td>refund.failed</td><td>initiated refund on your account eventually failed</td></tr><tr><td>chargeback.success</td><td>Accepted chargeback on your account was successful</td></tr><tr><td>chargeback.failed</td><td>Accepted chargeback failed eventually after processing</td></tr></tbody></table>



[^1]: https://pilot.vacepay.com/login
