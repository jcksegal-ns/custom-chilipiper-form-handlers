# Custom Chili Piper Booking Handlers

Scripts for triggering [Chili Piper](https://www.chilipiper.com/) booking flows after form submissions. Designed for deployment via Google Tag Manager.

## Scripts

### HubSpot (`HubSpot-ChilipiperBooker.html`)

Listens for HubSpot form submissions and triggers Chili Piper. Supports both:
- **HubSpot Forms v4** - Uses native `hs-form-event:on-submission:success` events
- **HubSpot Forms v3 (legacy)** - Uses `postMessage` callbacks

### Marketo (`Marketo-ChilipiperBooker.html`)

Hooks into Marketo's `MktoForms2.whenReady()` API to trigger Chili Piper on form success.

### HTML Forms (`HTML-ChilipiperBooker.html`)

Works with standard HTML forms including WebFlow, WordPress, and custom forms. Uses event delegation to capture form submissions matching a configurable CSS selector.

## Configuration

All scripts have a configuration section at the top. Modify only the settings above the "DO NOT MODIFY BELOW THIS LINE" comment.

| Setting | Description |
|---------|-------------|
| `cpTenantDomain` | Your Chili Piper subdomain |
| `cpRouterName` | Your Chili Piper router name |
| `enableGTMEvents` | Toggle GTM dataLayer event tracking |
| `gtmEvents` | Customize GTM event names for each callback |
| `shouldSubmitForm()` | Filter which forms trigger Chili Piper |
| `formSelector` | (HTML only) CSS selector for target forms |

## Deployment

1. Copy the appropriate script for your form platform
2. Update the configuration settings at the top
3. Deploy via Google Tag Manager (or embed directly on your page)

## Documentation

- [Chili Piper Concierge JS API](https://help.chilipiper.com/hc/en-us/articles/32588330506643-Concierge-Snippet-and-JS-API)
- [HubSpot Global Form Events (v4)](https://developers.hubspot.com/docs/api-reference/global-form-events/guide)
- [Marketo Forms API Reference](https://experienceleague.adobe.com/en/docs/marketo-developer/marketo/javascriptapi/forms-api-reference)
