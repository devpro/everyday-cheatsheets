# NPM

→ [npmjs.com](https://www.npmjs.com/)

## Installation

→ [nodejs.org](https://nodejs.org/)

## CLI

```bash
# checks Node.js version
node -v

# checks NPM version
npm -v

# if issues, clears the cache
npm cache clean --force

# updates npm
npm install -g npm
npm update -g

# review dependency on one package (natives for example)
npm ls natives
```

## Configuration

- List registries: `npm config list registry`
- Reset to the default registry: `npm config set registry https://registry.npmjs.org/`
- See peer dependencies: `npm view tsickle@0.34.3 peerDependencies`

### Working with MyGet

- [MyGet NPM support](https://docs.myget.org/docs/reference/myget-npm-support)
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
