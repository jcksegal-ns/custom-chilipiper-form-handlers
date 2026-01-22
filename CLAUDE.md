# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

Custom Chili Piper booking handler scripts for HubSpot, Marketo, and HTML form integrations. Deployed via Google Tag Manager to trigger Chili Piper's meeting scheduler after form submissions.

## Architecture

Three standalone HTML/JavaScript snippets:

- **HubSpot-ChilipiperBooker.html**: Supports both HubSpot Forms v4 (native `hs-form-event:on-submission:success` events) and v3 legacy (`postMessage` callbacks).

- **Marketo-ChilipiperBooker.html**: Uses Marketo's `MktoForms2.whenReady()` API to hook into form success events. Includes fallback initialization if the Marketo library loads after the script.

- **HTML-ChilipiperBooker.html**: Uses event delegation on the `submit` event to capture standard HTML form submissions. Targets forms via configurable CSS selector (`formSelector`).

All scripts call `ChiliPiper.submit()` with `trigger: 'ThirdPartyForm'` and optionally push GTM dataLayer events.

## Code Structure

Each script is divided into two sections:

1. **Configuration section** (top): All user-modifiable settings including `cpTenantDomain`, `cpRouterName`, GTM event settings, and `shouldSubmitForm()` filter function.

2. **Implementation section** (below "DO NOT MODIFY BELOW THIS LINE"): Core logic that should not be edited.

When making changes:
- Add new configuration options above the divider line
- Keep implementation logic below the divider line
- Maintain consistency between all scripts where possible
