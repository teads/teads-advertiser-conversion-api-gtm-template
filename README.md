# teads-advertiser-conversion-api-gtm-template
Teads template for Google Tag Manager Server-to-Server for Conversion API

To update this template you can find the appropriate documentation here: https://developers.google.com/tag-manager/templates/gallery#update_your_template

## Consent Settings

This template supports [Google Consent Mode v2](https://developers.google.com/tag-platform/tag-manager/server-side/consent-mode?hl=fr#server-container-server-side). The **Consent Settings** section provides a configurable checkbox:

- **Require ad_storage consent** (default: ON) — Reads the `x-ga-gcs` event data field forwarded by the GA4 client and checks `ad_storage` consent before firing.

### Behavior

- **Consent granted**: The tag fires normally and sends conversion data to the Teads Conversion API.
- **Consent denied**: The tag returns successfully without sending any HTTP request — no data reaches Teads.
- **Checkbox OFF**: The tag fires unconditionally (backward-compatible behavior).
- **No consent mode configured** (no `x-ga-gcs` in event data): The tag fires normally — consent mode is treated as not applicable.

### Server-side GTM constraints

`isConsentGranted` is a client-side-only GTM API that does not exist in server-side containers. The `access_consent` permission is also unavailable for server containers. The server-side equivalent is parsing the `x-ga-gcs` field forwarded by the GA4 client.

`x-ga-gcs` format: `"G" + version_digit + ad_storage(0/1) + analytics_storage(0/1)` — e.g. `"G100"` means `ad_storage` denied. `ad_storage` is always at index `[2]`. Note: `ad_user_data` is not encoded in `x-ga-gcs`.

### References

- https://developers.google.com/tag-platform/tag-manager/server-side/api?hl=fr
- https://developers.google.com/tag-platform/tag-manager/server-side/consent-mode?hl=fr#server-container-server-side
- https://support.google.com/analytics/answer/9976101?hl=fr#aivsbi1
- https://medium.com/@aristomenis.georgiopoulos/server-side-gtm-consent-mode-v2-the-2026-setup-guide-most-people-get-wrong-ef9d2ae81438
- https://consentcheck.online/how-to-pass-consent-cmp-to-server-side-gtm
