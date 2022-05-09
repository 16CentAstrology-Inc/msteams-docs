---
title: Extend Teams apps across Microsoft 365 (preview)
description: Extend your Teams app experiences to other high-usage areas of Microsoft 365 
ms.date: 05/24/2022
ms.topic: overview
ms.custom: m365apps
ms.localizationpriority: high
---
# Extend Teams apps across Microsoft 365

With the latest releases of [Microsoft Teams JavaScript client SDK](using-teams-client-sdk-preview.md) (version 2.0.0), [Team App manifest](../resources/schema/manifest-schema.md) (version 1.13), and [Teams Toolkit](../toolkit/visual-studio-code-overview.md), you can build and update Teams apps to run in other high-usage Microsoft 365 products and publish them to [Microsoft AppSource](https://appsource.microsoft.com/).

Extending your Teams app across Microsoft 365 provides a streamlined way to deliver cross-platform apps to an expanded user audience: from a single codebase, you can create app experiences tailored for Teams, Outlook, and Office environments. End users won't have to leave the context of their work to use your app, and administrators benefit from a consolidated management and deployment workflow.

The Teams app platform continues to evolve and expand holistically into the Microsoft 365 ecosystem. Here's the current support of Teams app platform elements across Microsoft 365 (Teams, Outlook, and Office as application hosts):

|          | App manifest element | Teams support |Outlook* support | Office* support | Notes |
|--|--|--|--|--|--|
| [**Tabs**](../tabs/what-are-tabs.md) (personal scope)    |`staticTabs`  | Desktop, Web, Mobile | Desktop (Beta Channel), Web (Targeted Release) | Desktop, Web (Targeted Release)| Channel and group scope not yet supported for M365. See [notes](../tabs/how-to/using-teams-client-sdk.md#microsoft-365-support-running-teams-apps-in-office-and-outlook).
| [**Message extensions**](../messaging-extensions/what-are-messaging-extensions.md) (search-based)| `composeExtensions` | Desktop, Web, Mobile| Desktop (Beta Channel), Web (Targeted Release)| - |Action-based not yet supported for M365. See [notes](extend-m365-teams-message-extension.md#preview-your-message-extension-in-outlook). |
| [**Graph connectors**](/microsoftsearch/connectors-overview)| `graphConnector` | Desktop, Web, Mobile| | | See [notes](#graph-connectors-preview)
| [**Office Add-ins**](/office/dev/add-ins/develop/json-manifest-overview) (preview) | `extensions` | | Desktop, Web | | Only available in [devPreview](../resources/schema/manifest-schema-dev-preview.md) manifest version. See [notes](#office-add-ins-preview).|

\* The [M365 Targeted release](/microsoft-365/admin/manage/release-options-in-office-365) option requires admin opt-in for the entire organization or selected users.

For guidance on Teams app manifest and SDK versioning guidance and further details on current Teams platform capability support across M365, see the [Teams JavaScript client SDK overview](../tabs/how-to/using-teams-client-sdk.md).

> [!NOTE]
> We welcome your feedback and issue reporting as you expand Teams apps to run across Microsoft 365 ecosystem! Please use the regular [Microsoft Teams developer community channels](/microsoftteams/platform/feedback).

## Personal tabs and messaging extensions in Outlook and Office

Reach your users where they are, right in the context of their work by extending your web app as a Teams personal tab application that runs in both Outlook and Office.

:::image type="content" source="images/outlook-office-teams-personal-tab.png" alt-text="Personal tab running in Outlook, Office, and Teams":::

You can also extend your search-based Teams message extensions to Outlook on the web and Windows desktop, enabling your customers to search and share results through the compose message area of Outlook, in addition to Microsoft Teams clients.

:::image type="content" source="images/outlook-teams-messaging-ext.png" alt-text="Message extension running in Outlook and Teams":::

Building your app with the latest [Teams app manifest](../resources/schema/manifest-schema.md) and [Teams JavaScript client SDK](using-teams-client-sdk-preview.md) provides you with a consolidated development process. By enabling you to deliver a streamlined deployment, installation, and admin experience for your customers, you can expand the potential reach and usage of your app.

## Use Teams app manifest across Microsoft 365

With an aim toward simplifying and streamlining the Microsoft 365 developer ecosystem, we're continuing to expand the Teams app manifest into other areas of Microsoft 365 with the following.

### Graph connectors

With Microsoft Graph connectors, your organization can index third-party data so that it appears as Microsoft Search results, expanding the types of searchable content sources in your Teams apps.
To learn more, see [Microsoft Graph connectors overview for Microsoft Search](/microsoftsearch/connectors-overview).

To get started with graph connectors in Teams apps, check out the [Teams Toolkit Graph connectors sample](https://aka.ms/teamsfx-graph-connector-sample) and [Microsoft Teams Developer preview manifest schema](../resources/schema/manifest-schema-dev-preview.md) reference.

### Office Add-ins (preview)

You can now define and deploy Office Add-ins in the [developer preview version](../resources/schema/manifest-schema-dev-preview.md) of the Microsoft Teams app manifest. Currently this preview is limited to Outlook Add-ins running on subscription Office for Windows.

To learn more, see [Teams manifest for Office Add-ins (preview)](/office/dev/add-ins/develop/json-manifest-overview). Get started and [Build an Outlook add-in with a Teams manifest(preview)](/office/dev/add-ins/quickstarts/outlook-quickstart-json-manifest).

## Microsoft AppSource submission

Join the growing number of production Teams apps in the [Microsoft AppSource](https://appsource.microsoft.com/) store with expanded support for Outlook and Office preview (Targeted Release) audiences. The app [submission process for  Teams apps enabled for Outlook and Office](../concepts/deploy-and-publish/appsource/publish.md) is the same as for traditional Teams apps; the only difference is you'll [reference version 1.13](../tabs/how-to/using-teams-client-sdk.md) of the Teams app manifest schema in your app package, which introduces support for Teams apps that run across M365.

Once published as a M365-enabled Teams app, your app will be discoverable as an installable app from the Outlook and Office app stores in addition to Teams. When running in Outlook and Office, your app uses the same permissions granted in Teams. Teams admins can [Manage access to Teams apps across Microsoft 365](/MicrosoftTeams/manage-third-party-teams-apps) for users in their organization.

:::image type="content" source="images/outlook-office-app-install.png" alt-text="Outlook and Office.com install screens for the SurveyMonkey and MURAL Teams apps":::

## Next steps

Set up your dev environment to build Teams apps for Microsoft 365:

> [!div class="nextstepaction"]
> [Install prerequisites](prerequisites.md)
