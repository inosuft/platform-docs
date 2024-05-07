# 🏉 API Rate Limits

Vacepay permits 3000 API calls every 24 hours. A response with the HTTP error code 429 will be returned for calls that go beyond this cap. See example response below

```javascript
{
    message: "You have exceeded the number of requests in 24 hrs limit!"
}
```

A good way to handle limits is to build a retry mechanism around the 429 status codes when received.
