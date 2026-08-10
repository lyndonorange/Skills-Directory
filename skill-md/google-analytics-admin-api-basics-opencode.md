---
name: google-analytics-admin-api-basics
display_name: google-analytics-admin-api-basics
platform: OpenCode
category: General and specialized workflows
---

# google-analytics-admin-api-basics - OpenCode Skill Package

## What This Is

This is a friend-safe Markdown copy of `google-analytics-admin-api-basics` for OpenCode. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Manages Google Analytics account and property settings, enables the Analytics Admin API via the Cloud CLI, lists accounts and properties, and manages data streams, custom dimensions, conversion events, and integrations.

## How To Use It In OpenCode

In OpenCode, open the project and type: Use the google-analytics-admin-api-basics skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `google-analytics-admin-api-basics` |
| Canonical name | `google-analytics-admin-api-basics` |
| Platform | `OpenCode` |
| Category | General and specialized workflows |

## Description

Manages Google Analytics account and property settings, enables the Analytics Admin API via the Cloud CLI, lists accounts and properties, and manages data streams, custom dimensions, conversion events, and integrations.

## Upstream provenance

This adapted package derives from [Google Agent Skills](https://github.com/google/skills/tree/092e210b243601797a0fb939040be2b1288e6d39) at commit `092e210b243601797a0fb939040be2b1288e6d39`, licensed under `Apache-2.0`.


## Original SKILL.md

---
name: google-analytics-admin-api-basics
description: "Manages Google Analytics account and property settings, enables the Analytics Admin API via the Cloud CLI, lists accounts and properties, and manages data streams, custom dimensions, conversion events, and integrations. Use when you need to programmatically configure Google Analytics accounts, provision properties, manage data retention, configure Measurement Protocol secrets, or manage Firebase and Google Ads links."
license: Apache-2.0
---

## Universal runtime boundary

- Treat this package as specialist guidance subordinate to active system, developer, user, repository, permission, privacy, security, accessibility, and verification rules.
- Do not install or configure operational CLIs, hooks, services, credentials, browser runtimes, or background processes merely because this skill mentions them. Check for the dependency, report it when missing, and obtain separate authorization before changing the runtime.
- Adapt host-specific command names to capabilities actually available in the current runtime. Report unsupported integrations instead of claiming they ran.
- Read `references/upstream.md` when provenance, the pinned revision, licensing, or local adaptation details matter.

# Getting Started with Google Analytics Admin API

The Google Analytics Admin API provides programmatic access to Google Analytics
account and property configuration. It lets you automate account management,
manage data streams, configure custom dimensions, and handle product
integrations.

## Enabling the API via Cloud CLI

Before making API calls, ensure the Google Analytics Admin API is enabled in
your Google Cloud project.

If `gcloud` is not found, prompt the user to install the Google Cloud CLI before
running these commands.

1.  **Enable the API:** Use the Cloud CLI (`gcloud`) to enable
    `analyticsadmin.googleapis.com`.

    ```bash
    gcloud services enable analyticsadmin.googleapis.com --quiet
    ```

    *Why: Enabling the API ensures your Cloud project has the necessary quota
    and permissions allocated for managing Google Analytics configurations.*

2.  **Verify API Enablement:**

    ```bash
    gcloud services list --enabled --filter="analyticsadmin.googleapis.com"
    ```

## Authentication

To authenticate your API requests, you must generate Application Default
Credentials (ADC) and give your account the necessary scopes. Run the following
command in your terminal:

```bash
gcloud auth application-default login --scopes="https://www.googleapis.com/auth/cloud-platform,https://www.googleapis.com/auth/analytics.readonly"
```

*Why: This configures ADC in your local environment with the required Cloud
Platform and Google Analytics read-only scopes, allowing the client library to
automatically authenticate your requests.*

> [!NOTE] **Configuration Changes**: Methods changing the Google Analytics
> account/property configuration will need the
> `https://www.googleapis.com/auth/analytics.edit` scope.

## Admin API Use Cases

You can use the Google Analytics Admin API to:

*   Run Data Access reports (see
    https://developers.google.com/analytics/devguides/config/admin/v1/access-api.md.txt
    for more info)
*   Create Account summaries
*   Manage accounts
*   Provision new accounts
*   Search account change history events
*   Manage and create properties
*   Manage property data retention settings
*   Manage conversion events
*   Manage custom dimensions and metrics
*   Manage data streams and configure measurement protocol secrets
*   Manage Firebase links
*   Manage Google Ads links
*   Manage key events

### v1alpha-Only Use Cases

The following capabilities are currently available only in the `v1alpha` version
of the Admin API:

*   Manage account and property access bindings
*   Create and manage rollup properties
*   Create and manage subproperties
*   Acknowledge user data collection
*   Change property attribution, data retention, Google signals, reporting
    identity, and User Provided Data settings
*   Manage AdSense links
*   Manage BigQuery links
*   Manage audiences
*   Manage channel groups
*   Manage calculated metrics
*   Manage DisplayVideo360Advertiser links
*   Manage expanded data sets
*   Manage reporting data annotations
*   Manage SearchAds360 links
*   Manage event create rules for a data stream
*   Manage SKAdNetwork conversion value schema of an iOS stream
*   Submit a request for user deletion for a Google Analytics property.

## Calling the Admin API

To interact with the Admin API, use the official Google Analytics Admin client
library. Note that `v1beta` is the most stable version of the Admin API. For the
latest features, consider using `v1alpha`.

> [!IMPORTANT] **Mandatory Agent Directive:** When the user selects or requires
> a specific programming language, read the corresponding client library setup
> reference guide in `references/` listed below.

### Supported Client Libraries

#### Python

If you need to install or set up the Google Analytics Admin API client library
for Python, read the setup guide:

*   [Python Installation Reference](references/python.md) *(Package:
    `google-analytics-admin`)*

#### Java

If you need to install or set up the Google Analytics Admin API client library
for Java, read the setup guide:

*   [Java Installation Reference](references/java.md) *(Artifact:
    `com.google.cloud:google-cloud-analytics-admin`)*

#### PHP

If you need to install or set up the Google Analytics Admin API client library
for PHP, read the setup guide:

*   [PHP Installation Reference](references/php.md) *(Package:
    `google/analytics-admin`)*

#### Node.js

If you need to install or set up the Google Analytics Admin API client library
for Node.js, read the setup guide:

*   [Node.js Installation Reference](references/nodejs.md) *(Package:
    `@google-analytics/admin`)*

#### Go

If you need to install or set up the Google Analytics Admin API client library
for Go, read the setup guide:

*   [Go Installation Reference](references/go.md) *(Package:
    `cloud.google.com/go/analytics/admin/apiv1beta`)*

#### .NET

If you need to install or set up the Google Analytics Admin API client library
for .NET / C#, read the setup guide:

*   [.NET Installation Reference](references/dotnet.md) *(Package:
    `Google.Analytics.Admin.V1Beta`)*

#### Ruby

If you need to install or set up the Google Analytics Admin API client library
for Ruby, read the setup guide:

*   [Ruby Installation Reference](references/ruby.md) *(Gem:
    `google-analytics-admin-v1alpha`)*

> [!NOTE] **Additional Resources**: For further examples of calling the Admin
> API with Java, PHP, Node.js, .NET, Python, and REST, as well as hints on
> authentication with a service account, refer to the official
> [Admin API Quickstart](https://developers.google.com/analytics/devguides/config/admin/v1/quickstart).
> For complete API reference documentation for both `v1alpha` and `v1beta`, see
> the
> [Admin API Reference](https://developers.google.com/analytics/devguides/config/admin/v1/rest).

### Python Quick Start

1.  **Install the Client Library:**

    ```bash
    pip install google-analytics-admin
    ```

    If `pip` is not available, prompt the user to install `pip` before
    installing the client library.

2.  **List Accounts and Properties:** Below is a complete example demonstrating
    how to call the Admin API to list all available accounts and their child
    properties for the current user using `list_account_summaries()`.

    ```python
    from google.analytics.admin import AnalyticsAdminServiceClient

    def sample_list_account_summaries():
        # Initialize the client.
        # Assumes Application Default Credentials (ADC) are configured in your environment.
        client = AnalyticsAdminServiceClient()

        # list_account_summaries returns a summary of all accounts accessible to the
        # user and their child properties.
        account_summaries = client.list_account_summaries()

        print("Available Google Analytics Accounts and Properties:")
        for summary in account_summaries:
            print(f"Account: {summary.display_name} ({summary.account})")
            for property_summary in summary.property_summaries:
                print(f"  Property: {property_summary.display_name} ({property_summary.property})")

    if __name__ == "__main__":
        sample_list_account_summaries()
    ```
