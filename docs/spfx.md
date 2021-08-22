# SharePoint Framework (SPFx)

> Page and web part model that provides full support for client-side SharePoint development, easy integration with SharePoint data, and extending Microsoft Teams.

→ [docs.microsoft.com/spfx](https://docs.microsoft.com/en-us/sharepoint/dev/spfx/sharepoint-framework-overview)

## Learn

### History

* **2017**: Microsoft introduced the SharePoint Framework as the recommended way to customize and extend SharePoint Online

### Key elements

* SharePoint Framework is modern client-side development
* [**Extensions**](https://docs.microsoft.com/en-us/sharepoint/dev/spfx/extensions/overview-extensions)
  * Types: Application customizers, Field customizers, Command sets
* **Workbench**: a special SharePoint page that contains a single canvas that developers can add their web parts to. There are two different workbench options: local and hosted.
* **Web parts**
  * Property pane
    * The property pane has two different modes: reactive and non-reactive
* JavaScript agnostic but can be used with a framework (React in particular)

### Read further

* [SharePoint Framework UI components](./spfx-ui-components.md)

### Learning path

1. [Introduction to customizing and extending SharePoint](https://docs.microsoft.com/en-us/learn/modules/intro-sharepoint-framework/)

2. [Get started with the SharePoint Framework](https://docs.microsoft.com/en-us/learn/modules/sharepoint-spfx-get-started/) ([code](https://github.com/SharePoint/sp-dev-training-spfx-getting-started), [video](https://www.youtube.com/watch?v=_Pt5cnU4MpU&list=PLR9nK3mnD-OV-RPXQ3Lco845qoEy7VJoc))

3. [Develop web parts with the SharePoint Framework](https://docs.microsoft.com/fr-fr/learn/modules/sharepoint-spfx-web-parts/)

4. [Enable SharePoint Framework web part configuration with property panes](https://docs.microsoft.com/en-us/learn/modules/sharepoint-spfx-web-part-property-pane/) ([code](https://github.com/SharePoint/sp-dev-training-spfx-webpart-proppane), [video](https://www.youtube.com/watch?v=4QLY6z3RGug&list=PLR9nK3mnD-OV-RPXQ3Lco845qoEy7VJoc))

5. [Work with SharePoint Content using the SharePoint Framework](https://docs.microsoft.com/en-us/learn/modules/sharepoint-spfx-spcontent/) ([code](https://github.com/SharePoint/sp-dev-training-spfx-spcontent), [video](https://www.youtube.com/watch?v=0OiC7AzoCVI&list=PLR9nK3mnD-OV-RPXQ3Lco845qoEy7VJoc))

6. [Extend the SharePoint user interface with SharePoint Framework extensions](https://docs.microsoft.com/en-us/learn/modules/sharepoint-spfx-extensions/) ([code](https://github.com/SharePoint/sp-dev-training-spfx-extensions), [video](https://www.youtube.com/watch?v=85DlxhbIK9I&list=PLR9nK3mnD-OV-RPXQ3Lco845qoEy7VJoc))

7. [Leverage Microsoft Graph & third-party APIs](https://docs.microsoft.com/en-us/learn/modules/sharepoint-spfx-graph-3rd-party-apis/) ([code](https://github.com/SharePoint/sp-dev-training-spfx-graph-3rdpartyapis), [video](https://www.youtube.com/watch?v=0zVtDn0ckBM&list=PLR9nK3mnD-OV-RPXQ3Lco845qoEy7VJoc))

8. [Deploy SharePoint Framework Components to Production](https://docs.microsoft.com/en-us/learn/modules/sharepoint-spfx-deployment/?ns-enrollment-type=LearningPath&ns-enrollment-id=learn-m365.sharepoint-associate) ([code](https://github.com/SharePoint/sp-dev-training-spfx-deployment), [video](https://www.youtube.com/watch?v=DLi6ZviEIJ8))

10. [Use Office UI Fabric React components in your SharePoint client-side web part](https://docs.microsoft.com/en-us/sharepoint/dev/spfx/web-parts/get-started/use-fabric-react-components) ([video](https://www.youtube.com/watch?v=kNrYd8nYaZY))

11. [Consume the Microsoft Graph in the SharePoint Framework](https://docs.microsoft.com/en-us/sharepoint/dev/spfx/use-aad-tutorial)

### Code samples

* [pnp/sp-starter-kit](https://github.com/pnp/sp-starter-kit)
* [PnP SharePoint Framework Client-Side Extension Samples](https://pnp.github.io/sp-dev-fx-extensions/)
  * [pnp/sp-dev-fx-extensions](https://github.com/pnp/sp-dev-fx-extensions)
* [PnP SharePoint Framework Client-Side Web Part Samples](https://pnp.github.io/sp-dev-fx-webparts/)
  * [pnp/sp-dev-fx-webparts](https://github.com/pnp/sp-dev-fx-webparts)
* [pnp/sp-dev-fx-library-components](https://github.com/pnp/sp-dev-fx-library-components)

### Usecases

#### Persistence

* [Improve performance in SharePoint provider-hosted add-ins](https://docs.microsoft.com/en-us/sharepoint/dev/solution-guidance/improve-performance-in-sharepoint-provider-hosted-add-ins)

#### API calls

* [Connect to Azure AD-secured APIs in SharePoint Framework solutions](https://docs.microsoft.com/en-us/sharepoint/dev/spfx/use-aadhttpclient)

#### Logging

* Default logging works on local workbench but not on SharePoint Online workbench
  * Install the PnP library

```
npm install @pnp/logging
```

## Develop

→ [Set up your SharePoint Framework development environment](https://docs.microsoft.com/en-us/sharepoint/dev/spfx/set-up-your-development-environment)

### Command line

* [NPM](./npm.md)

```bash
# installs Yeoman
npm install --global yo

# installs Gulp
npm install --global gulp

# installs SharePoint Framework generator
npm install --global @microsoft/generator-sharepoint
```

* [Microsoft SPFx Yeoman generator](https://www.npmjs.com/package/@microsoft/generator-sharepoint)

```bash
# creates a SharePoint Framework client-side web part
yo @microsoft/sharepoint
```

* [PnP SPFx Yeoman generator](https://pnp.github.io/generator-spfx/) ([GitHub](https://github.com/pnp/generator-spfx/))

* Gulp

```bash
# builds local resources
gulp build

# starts the local web server without launching the browser
gulp serve --nobrowser

# opens configuration to edit initialPage (workbench URL, local or hosted)
vi config/serve.json

# bundles the solution
gulp bundle --ship

# packages the solution
gulp package-solution --ship

# tracks the generated SharePoint package
ls /sharepoint/solution/*.sppkg
```

Read more about Gulp commands: [Explore a SharePoint Framework project](https://docs.microsoft.com/en-us/learn/modules/sharepoint-spfx-web-parts/2-explore-project)
