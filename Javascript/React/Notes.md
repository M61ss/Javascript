# React

## Include React from HTML

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8" />
    <title>Hello World</title>
    <!-- Includes the React library -->
    <script src="https://unpkg.com/react@18/umd/react.development.js"></script>
    <!-- Manages React elements rendering on real DOM -->
    <script src="https://unpkg.com/react-dom@18/umd/react-dom.development.js"></script>

    <!-- Don't use this in production: -->
    <!-- Allows to use JSX in Javascript -->
    <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
  </head>
  <body>
    <div id="root"></div>
    <script type="text/babel">
    
      function MyApp() {
        return <h1>Hello, world!</h1>;
      }

      const container = document.getElementById('root');
      const root = ReactDOM.createRoot(container);
      root.render(<MyApp />);

    </script>
    <!--
      Note: this page is a great way to try React but it's not suitable for production.
      It slowly compiles JSX with Babel in the browser and uses a large development build of React.

      Read this page for starting a new React project with JSX:
      https://react.dev/learn/start-a-new-react-project

      Read this page for adding React with JSX to an existing project:
      https://react.dev/learn/add-react-to-an-existing-project
    -->
  </body>
</html>
```

## React element

```html
<div id="root"><!-- Empty container --></div>
<script type="text/babel">
    const elem = <p>Hello <strong>React</strong>!</p>;      // Definition
    ReactDOM.render(elem, document.getElementById('root')); // Rendering
</script>
```

`ReactDOM.render` takes the first element as **React element** and puts it inside the passed **container**, which is necessary for React to create corrispondence between virtual and real DOMs.

As we can notice, the `<div>` is initially empty. Assigning it to React engine, the real DOM, the `<div>`, is updated adding changes apported by Javascript code. In this example, React simply add a static element to the `<div>`, producing a result equivalent to this:

```html
<div id="root">
    <p>Hello <strong>React</strong>!</p>
</div>
``` 

## React component

Components are similar to objects: each of them has a specific role inside the UI, so it manage user interactions only for a reduced piece of the whole UI.

### Function component

```js
function Car() {
    return <h2>I am a Car!</h2>;
}
ReactDOM.render(<Car />, document.getElementById('root'));
```

The function must to return a React element.

### Class component

It has addictional features than function components:

```js
class Car extends React.Component {
    render() {
        return <h2>Hi, I am a Car!</h2>;
    }
}
ReactDOM.render(<Car />, document.getElementById('root'));
```

It must implement the `render()` function, which must return a React element.

> [!TIP] Factory method
>
> Class can be created faster by a factory method:
>
> ```js
> var Car = React.createClass({
>   render: function() {
>     return <h2>Hi, I am a Car!</h2>;
>   }
> });
> ```

### `props`

`props` is an object which contains component's properties, which are immutable:

```js
function Car(props) {
    return <h2>I am a {props.colore} Car!</h2>;
}
ReactDOM.render(<Car colore="red"/>, document.getElementById('root'));
```

```js
class Car extends React.Component {
    render() { 
        return <h2>Hi, I am a Car. My name is {this.props.nome}</h2>;
    }
}
ReactDOM.render(<Car nome="Audi"/>, document.getElementById('root'));
```

## Installation

### Node.js

Install `nvm` (Node Version Manager):
   
```shell
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.0/install.sh | bash
```

> [!TIP]
> 
> Restart the terminal in order to load `nvm` and Node.js, then check if it is correctly loaded:
>
> ```shell
> nvm -v
> node -v
> ```

Update `nvm` to its last LTS version:

```shell
nvm install --lts
nvm use --lts
```

It automatically updates Node.js. 