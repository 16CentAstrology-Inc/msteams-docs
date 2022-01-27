---
title: Manage your apps with the Developer Portal
description: Learn how to configure, distribute, and manage your apps using the Developer Portal for Microsoft Teams.
keywords: getting started developer portal teams
ms.localizationpriority: medium
ms.topic: overview
ms.author: surbhigupta
---

# Manage your apps with the Developer Portal for Microsoft Teams

The <a href="https://dev.teams.microsoft.com" target="_blank">Developer Portal for Teams</a> is the primary tool for configuring, distributing, and managing your Microsoft Teams apps. With the Developer Portal, you can collaborate with colleagues on your app, set up runtime environments, and much more.

:::image type="content" source="../../assets/images/tdp/tdp_home_1.png" alt-text="Screenshot showing the home page of the Developer Portal for Teams.":::

## Register an app

The Developer Portal provides a couple ways to register a Teams app:

* Register a brand new app
* Import an existing app package

> [!NOTE]
> If you create an app using the [Microsoft Teams Toolkit for Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension), you can manage that app in the Developer Portal.

## Set up an environment

You can configure environments and global variables to help transition your app from your local runtime to production. Global variables are used across all environments.

**To set up an environment**

1. In the Developer Portal, select the app you're working on.
2. Go to the **Environments** page and select **+ Add an environment**.
3. Select **+ Add a variable** to create configuration variables for your environment.

**To use variables**

Use the variable names instead of hard-coded values to set your app configurations.

1. Enter `{{` in any field in the Developer Portal. A dropdown with all the variables you've created for the chosen environment along with the global variables appears.  
1. Before downloading your app package (for example, when getting ready to publish to the Teams store), select the environment you want to use. Your app configurations update automatically based on the environment. 

## Identify app owners

Each app includes an **Owners** page, where you can share your app registration with colleagues in your org. The **Contributor** role has the same permissions as the **Owner** role except the ability to delete an app.

## Configure your app's capabilities and other important metadata

A Teams app is a web app. Like all web apps, its source code is typically developed in an IDE or code editor and hosted somewhere in the cloud (like Azure).

To install and render your app in Teams, you must include a set of configurations that Teams recognizes. This has traditionally been done by crafting an app manifest, a JSON file that contains all the metadata Teams needs to display your app content. The Developer Portal abstracts this process and includes new features and tooling to help you be more successful.

## Test your app directly in Teams

The Developer Portal provides options for testing and debugging your app:

* On the **Overview** page, you can see a snapshot of whether your app's configurations validate against Teams store test cases.
* The **Preview in Teams** button lets you launch your app quickly in the Teams client for debugging.

## Distribute your app

From the Developer Portal, use the **Distribute** button to download an app package, publish to your org, or publish to the Teams store.

For more information, see [distribute your Teams app](~/concepts/deploy-and-publish/apps-publish-overview.md).

## Analyze your app's usage

On the Overview page, you can see the total number of active users for your app. These metrics are available for apps published to the Teams store or an org's app catalog through Developer Portal (or App Studio) and scoped to the app ID.

| Metric | Definition |
| :-----------------------| :------------------------------------------------------------------------------------------------------|
| *Monthly R30* | The default usage metric. It shows you the count of unique active users that used your app within that rolling 30-day window in UTC. |
| *Daily* | Shows you the count of unique active users that used your app in a given day in UTC. |

The app usage for a given day is reflected within 24-48 hours and usage data for new apps can take up to 3-5 days.

**To view additional details about your app(s) usage**

1. Go to <a href="https://dev.teams.microsoft.com" target="_blank">Developer Portal for Teams</a>.
1. Select **Apps** from the left pane.
1. Select the required app from the main page.
1. Select **Analytics** under the overview or select **View Details** under the active users card.

 :::image type="content" source="../../assets/images/tdp/dev-app-portal.PNG" alt-text="Portal":::

As you explore individual metrics on this page, you can use the **Filter** button to slice and dice all subsequent metrics by the following:

1. Aggregation Type
1. Platform
1. Operating system
1. Area

 :::image type="content" source="../../assets/images/tdp/dev-analytics-filter.PNG" alt-text="Filter":::

Once you have selected your desired filter(s), you can explore the following individual widgets:

* Usage by time period
* Usage by platform and OS
* Usage by retention state
* Usage intensity

### Usage by time period

This chart shows you the number of active users/tenants that have opened/used this app across different time periods.

 :::image type="content" source="../../assets/images/tdp/usage-by-time-period.png" alt-text="Period":::

| Metric | Definition |
| :-----------------------| :------------------------------------------------------------------------------------------------------|
| Monthly R30 | The count of distinct active users/tenants who have opened your app in a given RL30 (Rolling 30 day) period. |
| Monthly R28 | The count of distinct active users/tenants who have opened your app in a given RL28 (Rolling 28 day) period. |
| Weekly RL7| The count of distinct active users/tenants who have opened your app in a given RL7 (Rolling 7 day) period. |
| Daily | The count of distinct active users/tenants who have opened your app in a given RL1 (Rolling 1 day) period. |

### Usage by platform and OS

This chart shows your app(s) active usage across various endpoints – Windows, Mac, iOS, Android, and Web. The same user/tenant can use an app on multiple endpoints.

 :::image type="content" source="../../assets/images/tdp/usage-by-platform-OS.png" alt-text="Platform":::

### Usage by retention state

This chart lets you track four key retention/churn metrics of your app over time.

:::image type="content" source="../../assets/images/tdp/usage-by-retention-state.png" alt-text="Retention":::

| Metric | Definition |
| :-----------------------| :------------------------------------------------------------------------------------------------------|
| New Users/Tenants | Active users/tenants who are new (based on a historical start date of June 1, 2020). |
| Returning Users/Tenants | Active users/tenants who used your app during a given R30 time period and the previous R30 time period. |
| Resurrected Users/Tenants | Active users/tenants who used your app one or more times since June 1, 2020 but not in the immediately previous R30 time period. |
| Lapsed Users/Tenants | Active users/tenants who were not seen during a given R30 time period but were seen during the previous R30 time period. |

### Usage intensity

This chart shows you key usage intensity metrics of your app.

 :::image type="content" source="../../assets/images/tdp/usage-intensity.png" alt-text="Intensity":::

| Metric | Definition |
| :-----------------------| :------------------------------------------------------------------------------------------------------|
| Median Days Used per Month | The median numbers of days in which your app was opened in the last RL30 (Rolling 30 day) period. |
| % of 5+ Days Usage | The % of Active Users that have opened/used the app more than 5 days in the last RL30 (Rolling 30 day) period. |
| DAU/MAU | The ratio of the average number of unique users or tenants who used your app on each day divided by the Monthly Active Users for the selected R30 time period. It provides information on stickiness of user engagement with your app. |

### App dashboard

The App Dashboard shows you the latest value for each of these metrics and the Month over Month (MoM) change. You can select each of these rows to see trends over time.

 :::image type="content" source="../../assets/images/tdp/app-dashboard.png" alt-text="app":::

## Use tools to create app features

The Developer Portal also includes tools to help you build some key features of Teams apps. Some of these tools include:

* **Scene studio**: Design [custom Together Mode scenes](~/apps-in-teams-meetings/teams-together-mode.md) for Teams meetings.
* **Adaptive Cards editor**: Create and preview Adaptive Cards to include with your apps.
* **Microsoft identity platform management**: Register your apps with Azure Active Directory to help users sign in and provide access to APIs.

## See also

[Include a SaaS offer with your Microsoft Teams app](~/concepts/deploy-and-publish/appsource/prepare/include-saas-offer.md)
