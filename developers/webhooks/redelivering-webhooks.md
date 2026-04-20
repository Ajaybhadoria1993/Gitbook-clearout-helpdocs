# Redelivering Webhooks

This guide explains **Clearout's webhook retry logic and redelivery system**. When webhook deliveries fail, Clearout automatically retries with exponential backoff to ensure reliable delivery of your webhook events.

### Retry Overview

Clearout automatically retries failed webhook deliveries to ensure your application receives important event notifications. The retry system uses exponential backoff to handle temporary failures while avoiding overwhelming your server.

#### When Retries Occur <a href="#when-retries-occur" id="when-retries-occur"></a>

Webhook retries are triggered when:

* **HTTP Error Responses** - Your endpoint returns 4xx or 5xx status codes
* **Connection Timeouts** - Your server doesn't respond within 30 seconds
* **Network Issues** - Temporary network connectivity problems
* **Server Unavailability** - Your webhook endpoint is temporarily down

#### Retry Limits <a href="#retry-limits" id="retry-limits"></a>

The number of retry attempts depends on your account type

**Request Timeout**

Each webhook request has a maximum timeout of 30 seconds. If your endpoint doesn't respond within this time, the request will be considered failed and retried.

### Retry Schedule

Clearout uses exponential backoff for webhook retries, with delays that increase after each failed attempt:

| Attempt | Delay After Previous | Cumulative Time |
| ------- | -------------------- | --------------- |
| 1st     | Immediate            | 0 minutes       |
| 2nd     | 5 minutes            | 5 minutes       |
| 3rd     | 10 minutes           | 15 minutes      |
| 4th     | 20 minutes           | 35 minutes      |
| 5th     | 40 minutes           | 1 hour 15 min   |
| 6th     | 80 minutes           | 2 hours 35 min  |
| 7th     | 160 minutes          | 5 hours 15 min  |
| 8th     | 320 minutes          | 10 hours 35 min |
| 9th     | 640 minutes          | 21 hours 15 min |

**Exponential Backoff**

The retry delays approximately double with each attempt, providing time for temporary issues to resolve while preventing overloading your server with rapid retries.

### Failure Handling

When all retry attempts are exhausted, the webhook delivery is permanently marked as failed:

#### Permanent Failure <a href="#permanent-failure" id="permanent-failure"></a>

* **No More Retries** - After the maximum number of attempts, no further retries will be made
* **Failed Status** - The webhook delivery is marked as permanently failed
* **Event Logs** - The failure is recorded in your webhook delivery logs

#### Manual Retry <a href="#manual-retry" id="manual-retry"></a>

Manual retry functionality is not currently available. Once a webhook delivery is permanently failed, it cannot be manually retriggered through the dashboard.

### Monitoring

You can monitor webhook delivery status through the Clearout dashboard:

#### Event Logs <a href="#event-logs" id="event-logs"></a>

* **Access Logs** - Click the "View Event Logs" button in the webhook table
* **Delivery Status** - View success/failure status for each webhook delivery attempt
* **Response Details** - See HTTP status codes, response times, and error messages
* **JSON Payloads** - View the complete payload that was sent to your endpoint

#### Event Details <a href="#event-details" id="event-details"></a>

Click on any event in the logs to view detailed information including delivery status, response details, and the complete JSON payload.

#### Monitoring Recommendations <a href="#monitoring-recommendations" id="monitoring-recommendations"></a>

* **Regular Checks** - Monitor your webhook delivery logs regularly for failed deliveries
* **Success Rate Tracking** - Track your webhook delivery success rate over time
* **Alert Setup** - Consider setting up external monitoring for your webhook endpoints
* **Performance Monitoring** - Monitor response times to identify performance issues

### Best Practices

#### Webhook Endpoint Reliability <a href="#webhook-endpoint-reliability" id="webhook-endpoint-reliability"></a>

* **Fast Response** - Return HTTP 200 status codes quickly (within 30 seconds)
* **Idempotency** - Handle duplicate webhook deliveries gracefully
* **Error Handling** - Implement proper error handling for webhook processing
* **Queue Processing** - Use message queues for asynchronous webhook processing

#### Duplicate Delivery Handling <a href="#duplicate-handling" id="duplicate-handling"></a>

* **Event ID Tracking** - Use the `event_id` field to track processed events
* **Database Deduplication** - Store processed event IDs to prevent duplicate processing
* **Idempotent Operations** - Design your webhook handlers to be idempotent

#### Performance Optimization <a href="#performance-optimization" id="performance-optimization"></a>

* **Async Processing** - Process webhook data asynchronously when possible
* **Connection Pooling** - Use connection pooling for database operations
* **Resource Management** - Ensure adequate server resources for webhook processing
* **Monitoring** - Implement comprehensive monitoring and alerting

**Next Steps**

Now that you understand webhook retry behavior, check out our [FAQ](https://docs.clearout.io/webhooks/faq.html) for answers to common questions about webhooks.
