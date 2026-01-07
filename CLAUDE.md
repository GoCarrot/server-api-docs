# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is an Antora documentation component for the Teak Server API. It generates documentation that is integrated into a larger Teak documentation site via an Antora playbook.

The server API implementation being documented is located in `../carrot`.

## Build System

The documentation is built using Antora via CircleCI. The build uses the `teak/sdk-utils` orb with the `build-antora-playbook` command. There is no local build command in this repository - the Antora playbook that aggregates this component lives elsewhere.

To preview changes locally, you need clones of the related repositories (teak-unity, teak-ios, teak-android, teak-usage) and must run the Antora playbook from the parent documentation project.

## Documentation Structure

- `antora.yml` - Component descriptor (name: server-api, version: v2)
- `modules/ROOT/pages/` - Main documentation pages in AsciiDoc format
- `modules/ROOT/partials/` - Reusable AsciiDoc fragments (e.g., response templates)
- `modules/ROOT/nav.adoc` - Navigation structure

## Writing Documentation

### AsciiDoc Conventions

- Pages use AsciiDoc attributes for templating (e.g., `:response-code:`, `:response-body:`)
- Reusable response formatting is in `modules/ROOT/partials/response.adoc`
- Cross-references use the `xref:` macro with component prefixes (e.g., `xref:server-api::page$...`)
- External links to the dashboard use `window=_blank` attribute

### API Documentation Pattern

Each API endpoint document follows a consistent structure:
1. Endpoint metadata table (URL, method, content-type, rate limiting)
2. Description with links to dashboard configuration
3. Required parameters table
4. Optional parameters table
5. Success response with example
6. Error responses (404, 422, 429) using the `partial$response.adoc` template
