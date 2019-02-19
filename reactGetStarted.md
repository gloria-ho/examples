# Getting Started with React

* `npm init`

* `npm install -save react react-dom`

* `npm install --saveDev webpack webpack-dev-server webpack-cli`

* `npm install --saveDev babel-core babel-loader@7`

* `npm install --saveDev babel-preset-env babel-preset-react babel-preset-stage-0`

* `npm install --saveDev html-webpack-plugin`

* Create `.babelrc` file and add presets: `touch .babelrc`
```
{ "presets": ["env", "react", "stage-0"] }
```

* Create `/app` folder:  `mkdir app`

* Create `.html` file: `touch app/index.html`
```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>Hello, World!</title>
</head>
<body>
  <h1>Hello, World! Welcome to React.</h1>
  <div id="app"></div>
</body>
</html>
```

* Create `.js` file: `touch app/index.js`
```javascript
import React from 'react';
import ReactDom from 'react-dom';

// components
import App from './components/App';

ReactDom.render(
  <App />,
  document.getElementById('app')
);
```

* Edit `package.json` `"scripts"`, add `"build"` and `"dev"`:
```
"scripts": {
    "build": "webpack",
    "dev": "webpack-dev-server --define process.env.NODE_ENV='\"dev\"'",
    "test": "echo \"Error: no test specified\" && exit 1"
  }
```

* Create `/components` folder: `mkdir components`

* Create `App.js` file: `touch components/App.js`
```javascript
import React from 'react';

export default class App extends React.Component {
  constructor(props) {
    super(props);
  }

  render() {
    return (
      <div>
        Hello, react!
      </div>
    );
  }
}
```

## Notes on App.js

Class App is a *component*.

Classes are capitalized camel case.

At minimum, it renders a function that returns the output.

The return function can only have one outer container element.

Props example:
```javascript
import React from 'react';

export default class App extends React.Component {
  constructor(props) {
    super(props);
  }

  render() {
    return (
      <div>
        Hello, <Noun title='you' />.
        This is <Noun title='React' />.
      </div>
    );
  }
}

class Noun extends React.Component {
  // can create functions and variables in methods and call it in the return

  getName() {
    return this.props.title;
  }

  getStyle() {
    return { "border": "1px dashed red", "padding": "2px" };
  }

  render() {
    return (
      <span style={ this.getStyle() }>
        { this.getName() }
      </span>
    );
  }
}
```