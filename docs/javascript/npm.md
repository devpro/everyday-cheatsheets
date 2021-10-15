# NPM

> Node Package Manager

→ [npmjs.com](https://www.npmjs.com/)

## Installation

→ [nodejs.org](https://nodejs.org/)

## CLI

### Basic commands

```bash
# checks Node.js version
node -v

# checks NPM version
npm -v

# clears the cache (in case of issues)
npm cache clean --force

# updates npm
npm install -g npm
npm update -g

# displays dependencies on one package (natives in this example)
npm ls natives

# displays peer dependencies
npm view tsickle@0.34.3 peerDependencies
```

### Registries

```bash
# lists registries
npm config list registry

# resets to the default registry
npm config set registry https://registry.npmjs.org/
```

## Recipes

### Update packages

- Install and use [npm-check-updates](https://github.com/raineorshine/npm-check-updates)

```
# installs the tool globally
npm install -g npm-check-updates

# runs the tool against a project (in the project root directory)
ncu -u

# installs the packages from the newly updated package.json file
npm install
```

### Working with MyGet

- Read the documentation about [MyGet NPM support](https://docs.myget.org/docs/reference/myget-npm-support)
- Add another registry on MyGet: `npm config set @mycompany:registry https://www.myget.org/F/mycompany/npm/`
  - `npm install @mycopmpany/mypackage@1.0.1`
- Or add directly the zip url:

```json
{
  "dependencies": {
    "mypackage": "https://www.myget.org/F/mycompany/npm/mypackage/-/mypackage-1.0.0.tgz"
  }
}
```
