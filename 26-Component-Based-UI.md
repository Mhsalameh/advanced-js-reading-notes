# Component Based UI

React is a JavaScript library, that enables us to create UIs using multiple reusable components.

## React Hello world

```javascript
ReactDOM.createRoot(document.getElementById('root')).render(
  <h1>Hello, world!</h1>
);
```

this displays a heading saying Hello world!

## Introducing JSX

```javascript
const element = <h1>Hello, world!</h1>;
```

above syntax is called JSX, and it is a syntax extension to JavaScript. We recommend using it with React to describe what the UI should look like. JSX may remind you of a template language, but it comes with the full power of JavaScript. JSX produces React “elements”. We will explore rendering them to the DOM in the next section. Below, you can find the basics of JSX necessary to get you started.

**_Why JSX?_**

React doesn’t require using JSX, but most people find it helpful as a visual aid when working with UI inside the JavaScript code. It also allows React to show more useful error and warning messages.

**_Embedding Expressions in JSX_**

```javascript
const name = 'Josh Perez';
const element = <h1>Hello, {name}</h1>;
```

We declare a variable called name and then use it inside JSX by wrapping it in curly braces. You can put any valid JavaScript expression inside the curly braces in JSX. For example, 2 + 2, user.firstName, or formatName(user) are all valid JavaScript expressions.

**_JSX is an Expression Too_**

This means that you can use JSX inside of if statements and for loops, assign it to variables, accept it as arguments, and return it from functions

```javascript
function getGreeting(user) {
  if (user) {
    return <h1>Hello, {formatName(user)}!</h1>;
  }
  return <h1>Hello, Stranger.</h1>;
}
```

**_Specifying Attributes with JSX_**

Don’t put quotes around curly braces when embedding a JavaScript expression in an attribute. You should either use quotes (for string values) or curly braces (for expressions), but not both in the same attribute. `remember to use camelCase`

using quotes:

```javascript
const element = <a href='https://www.reactjs.org'> link </a>;
```

using curly braces

```javascript
const element = <img src={user.avatarUrl}></img>;
```

**_Specifying Children with JSX_**

closing tags < />

```javascript
const element = <img src={user.avatarUrl} />;
```

JSX tags with children

```javascript
const element = (
  <div>
    <h1>Hello!</h1>
    <h2>Good to see you here.</h2>
  </div>
);
```

**_JSX Prevents Injection Attacks_**

```javascript
const title = response.potentiallyMaliciousInput;
// This is safe:
const element = <h1>{title}</h1>;
```

It is safe to embed user input in JSX, by default, React DOM escapes any values embedded in JSX before rendering them. Thus it ensures that you can never inject anything that’s not explicitly written in your application. Everything is converted to a string before being rendered. This helps prevent XSS (cross-site-scripting) attacks.

## Rendering Elements

an element describes what you see on the screen, Unlike browser DOM elements, React elements are plain objects, and are cheap to create. React DOM takes care of updating the DOM to match the React elements.

**_Rendering an Element into the DOM_**

```html
<div id="root"></div>
```

We call this a “root” DOM node because everything inside it will be managed by React DOM.

To render a React element, first pass the DOM element to ReactDOM.createRoot(), then pass the React element to root.render():

```javascript
const element = <h1>Hello, world</h1>;
const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(element);
```

## bookmarks

- [react hello world](https://facebook.github.io/react/docs/hello-world.html)
- [introducing JSX](https://facebook.github.io/react/docs/introducing-jsx.html)
- [rendering elements](https://facebook.github.io/react/docs/rendering-elements.html)

- [sass cheatsheet](https://devhints.io/sass)
- [react cheatsheet](https://devhints.io/react)
- [another react cheatsheet](https://reactcheatsheet.com/)
