# SharePoint Framework UI components

Many components are already available, as open source libraries, to build nice UX/UI.

## JavaScript frameworks

Using a JavaScript framework is not mandatory but it can help having simple code. 

Options are:

* Angular
* [React](./reactjs.md) (recommended)

## Component libraries

### Office UI Fabric React (soon to be replaced by Fluent UI)

→ [developer.microsoft.com/fluentui](https://developer.microsoft.com/en-us/fluentui#/)

* Installation

```bash
npm install office-ui-fabric-react
```

* Introduction: [Use Office UI Fabric React components in your SharePoint client-side web part](https://docs.microsoft.com/en-us/sharepoint/dev/spfx/web-parts/get-started/use-fabric-react-components) ([Get Started with Fabric React](https://docs.microsoft.com/en-us/javascript/api/getstarted/getstartedpage?view=office-ui-fabric-react-latest))

* Catalog: [fluentui/controls/web](https://developer.microsoft.com/en-us/fluentui#/controls/web)

* Source code: [microsoft/fluentui](https://github.com/microsoft/fluentui)

* Examples: DocumentCard, Persona, [SearchBox](https://developer.microsoft.com/en-us/fluentui#/controls/web/searchbox)

### Microsoft Graph Toolkit components

> Library to use [Microsoft Graph](./microsoft-graph.md) Toolkit in SharePoint Framework solutions.

→ [SharePoint Framework library for Microsoft Graph Toolkit](https://docs.microsoft.com/en-us/graph/toolkit/get-started/mgt-spfx)

* Installation

```bash
npm install @microsoft/mgt-spfx

# for React
npm install @microsoft/mgt-react
```

* Getting started: [Build a SharePoint web part with the Microsoft Graph Toolkit](https://docs.microsoft.com/en-us/graph/toolkit/get-started/build-a-sharepoint-web-part)

* Examples: [Persona card](https://docs.microsoft.com/en-us/graph/toolkit/components/person-card)

### PnP (Microsoft 365 Patterns and Practices) components

* [Property pane controls](https://pnp.github.io/sp-dev-fx-property-controls) ([pnp/sp-dev-fx-property-controls](https://github.com/pnp/sp-dev-fx-property-controls))

```bash
npm install @pnp/spfx-property-controls --save --save-exact
```

* [React controls](https://pnp.github.io/sp-dev-fx-controls-react) ([pnp/sp-dev-fx-controls-react](https://github.com/pnp/sp-dev-fx-controls-react))

```bash
npm install @pnp/spfx-controls-react --save --save-exact
```
