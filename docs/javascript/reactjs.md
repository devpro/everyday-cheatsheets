# React

> A JavaScript library for building user interfaces

→ [reactjs.org](https://reactjs.org/), [GitHub](https://github.com/facebook/react)

## Learn

### Key elements

* [React.Component](https://reactjs.org/docs/react-component.html)

* [JSX](https://reactjs.org/docs/introducing-jsx.html) is a syntax extension to JavaScript. It is recommended to use it with React to describe what the UI should look like. JSX produces React “elements”.

### Quickstart

- [Create React App](https://create-react-app.dev/) ([Getting Started](https://create-react-app.dev/docs/getting-started))

```bash
# create the application and launch it (starts the development server)
npx create-react-app my-app
cd my-app
npm start

# later on...

# bundles the app into static files for production
npm run build

# starts the test runner
npm test

# removes the tool and copies build dependencies, configuration files and scripts into the app directory (no coming back)
npm run eject
```

### Tutorials

- [Getting started](https://reactjs.org/docs/getting-started.html)
- [Intro to React](https://reactjs.org/tutorial/tutorial.html)

### Testing

- [Testing Overview](https://reactjs.org/docs/testing.html)
- [Testing Recipes](https://reactjs.org/docs/testing-recipes.html)
- [Test Utilities](https://reactjs.org/docs/test-utils.html)

#### Jest

> Jest is a delightful JavaScript Testing Framework with a focus on simplicity.

→ [jestjs.io](https://jestjs.io/en/) ([Testing React Apps](https://jestjs.io/docs/en/tutorial-react))

Install dev dependancies: [testing-library/react](https://github.com/testing-library/react-testing-library), [testing-library/jest-dom](https://github.com/testing-library/jest-dom/)

```bash
npm install --save-dev @testing-library/react @testing-library/jest-dom
```
