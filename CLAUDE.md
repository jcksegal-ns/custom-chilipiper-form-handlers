# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

This repository contains custom Chili Piper booking handler scripts for marketing automation form integrations. These scripts are deployed via Google Tag Manager to trigger Chili Piper's meeting scheduler after form submissions.

## Architecture

Two standalone HTML/JavaScript snippets handle form submission events:

- **HubSpot-ChilipiperBooker.html**: Listens for HubSpot `hsFormCallback` window messages with `onFormSubmit` events, extracts lead data from form fields, and conditionally submits to Chili Piper based on field values.

- **Marketo-ChilipiperBooker.html**: Uses Marketo's `MktoForms2.whenReady()` API to hook into form success events and submit to Chili Piper.

Both scripts:
1. Load Chili Piper's marketing.js library
2. Configure tenant domain (`cpTenantDomain`) and router name (`cpRouterName`)
3. Call `ChiliPiper.submit()` with form data mapping
4. Push GTM dataLayer events for booking success/failure tracking

## Configuration

When customizing these scripts for a client:
- Replace `cpTenantDomain` with the client's Chili Piper subdomain
- Replace `cpRouterName` with the specific inbound router name
- For HubSpot: modify the conditional check (`lead.field_name == "Value"`) to target specific forms
