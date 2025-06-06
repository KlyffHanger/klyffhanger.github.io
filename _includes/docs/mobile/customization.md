{% if docsPrefix == 'pe/' %}
{% assign appPrefix = "Klyff PE" %}
{% else %}
{% assign appPrefix = "Klyff" %}
{% endif %}

{{appPrefix}} Mobile Application allows you to perform the following customizations **without code changes**:

- **[Customize home screen](/docs/{{docsPrefix}}mobile/customize-dashboards)**
- **[Customize device icons](/docs/{{docsPrefix}}mobile/customize-devices)**
- **[Setup device details dashboard](/docs/{{docsPrefix}}mobile/device-dashboard)**
- **[Setup alarm details dashboard](/docs/{{docsPrefix}}mobile/alarm-dashboard)**
- **[Configure mobile actions](/docs/{{docsPrefix}}mobile/mobile-actions)**
- **[Configure OAuth 2.0](/docs/{{docsPrefix}}mobile/oauth2)**
- **[Configure mobile app QR code settings](/docs/{{docsPrefix}}mobile/qr-code-settings/)**
{% if docsPrefix == 'pe/' %}
- **[Configure white-labeling](/docs/pe/mobile/white-labeling)**
- **[Configure self-registration](/docs/pe/mobile/self-registration)**
- **[Configure mobile app QR code settings](/docs/pe/mobile/qr-code-settings/)**
{% endif %}
