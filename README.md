# teads-advertiser-conversion-api-gtm-template
Teads template for Google Tag Manager Server-to-Server for Conversion API

To update this template you can find the appropriate documentation here: https://developers.google.com/tag-manager/templates/gallery#update_your_template

## Consent Settings

This template supports [Google Consent Mode](https://developers.google.com/tag-platform/tag-manager/server-side/consent-mode). The **Consent Settings** section provides a configurable checkbox:

- **Require ad_storage and ad_user_data consent** (default: ON) — Checks `isConsentGranted('ad_storage')` and `isConsentGranted('ad_user_data')` before firing. Both must be granted for the tag to send data to Teads.

### Behavior

- **Both consents granted**: The tag fires normally and sends conversion data to the Teads Conversion API.
- **Either consent denied**: The tag returns successfully without sending any HTTP request — no data reaches Teads.
- **Checkbox OFF**: The tag fires unconditionally (backward-compatible behavior).

### Reference

- [Google Consent Mode with Server-Side GTM](https://developers.google.com/tag-platform/tag-manager/server-side/consent-mode)
- [isConsentGranted API](https://developers.google.com/tag-platform/tag-manager/templates/api#isconsentgranted)
