# Technical tasks: Lumen & Clay Studio (demo)

> **Fictional demo.** The account, campaigns, ads and numbers below are made up to show what meta-ads-audit produces.

Only items tied to findings are listed.

## [ ] Conversions API for Purchase with a shared event_id
- **Why:** 1,585 browser purchase events, 0 server events.
- **Owner:** Developer · **Priority:** High
- **How:**
  1. Generate one event_id per order (for example the order number).
  2. Send it with the pixel: fbq('track', 'Purchase', {...}, {eventID: id}).
  3. Send the same event from the server with the same event_id, value, currency and hashed customer data.
  4. Check deduplication in Events Manager after 48 hours.

## [ ] Verify the domain and set Purchase as the top-priority event
- **Why:** Tracking finding: purchase signal depends on browser events only.
- **Owner:** Developer · **Priority:** Medium
- **How:**
  1. Business settings → Brand safety → Domains: add the domain and verify it with a DNS TXT record.
  2. Events Manager → Aggregated event measurement: put Purchase first.

## [ ] Check Event Match Quality manually
- **Why:** Data gap: the score was not available through the tools.
- **Owner:** Marketing · **Priority:** Medium
- **How:**
  1. Events Manager → your dataset → Overview → Purchase → Event match quality.
  2. If the score is below 6, add email and phone (hashed) to server events.

## [ ] Add the UTM template to all ads
- **Why:** 7 of 12 ads have no UTM parameters.
- **Owner:** Marketing · **Priority:** Low
- **How:**
  1. Ad → Tracking → URL parameters: utm_source=meta&utm_medium=paid_social&utm_campaign={{campaign.name}}&utm_content={{ad.name}}
  2. Use bulk edit to apply it to all active ads at once.

## Templates

### Pixel + Conversions API with a shared `event_id`
Browser:
```js
fbq('track', 'Purchase', { value: 64.00, currency: 'USD', content_ids: ['MUG-014'], content_type: 'product' }, { eventID: 'order_10482' });
```
Server (POST `/{dataset_id}/events`):
```json
{
  "data": [{
    "event_name": "Purchase",
    "event_time": 1763560000,
    "event_id": "order_10482",
    "action_source": "website",
    "event_source_url": "https://example.com/checkout/thank-you",
    "user_data": {
      "em": ["<sha256 of the lowercase email>"],
      "ph": ["<sha256 of the phone number, digits only>"],
      "client_ip_address": "<from the request>",
      "client_user_agent": "<from the request>",
      "fbp": "<_fbp cookie>",
      "fbc": "<_fbc cookie, if present>"
    },
    "custom_data": { "currency": "USD", "value": 64.00, "content_ids": ["MUG-014"], "content_type": "product" }
  }]
}
```
The `event_id` and `event_name` must match in both events so Meta counts the purchase once.

### UTM template
```
utm_source=meta&utm_medium=paid_social&utm_campaign={{campaign.name}}&utm_content={{ad.name}}
```
