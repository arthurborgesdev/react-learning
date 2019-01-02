# react-learning
Caderno digital com aprendizados sobre React

---

### Baseado nos escritos de Robin Wieruch

---

#### Native HTML elements

We have full control over them, as a input field in HTML has its own state. The text type in the input is captured into he `value` attribute.

Once the value of the input field has changed you can use the element callback `onChange()` to update the value in the internal component stat with `setState()`

Then:
* You can use the updated value in your input field.
* The internal component state is the single source of truth.
* The input field does not manage its own state anymore.

```
<input
  value={this.state.value}
  onChange={(event) => this.setState({ value: event.target.value })}
  type="text"
/>
```

---

### Essential React Libraries (2018)

Boilerplate decision:

* Minimal react boilerplate: `create-react-app`
* Gatsby.js for static websites
* Next.js for server side rendered React
* Minimal own boilerplate (needs solid understanding of React)
* Narrow down requirements and choose a minimal boilerplate to it

Utility:

* JS and ES6
* Lodash
* Ramda

Styling:

* plain and inline CSS
* classnames library
* CSS modules or Styled components

Assync Requests:

* fetch
* axios
* superagent

High Order Components:

* recompose for utility high order components
* recompose or utility library (Lodash, Ramda) for compose

Type Checking:

* PropTypes
* Flow (or TypeScript)

Formating:

* Reading a popular style guide (Airbnb)
* Prettier

UI Component Libraries:

* Semantic UI
* Material UI

State Management:

* React's local state
* Redux or MobX (only if it's needed)

Routing:

* React's conditional rendering
* React Router

Authentication:

* Firebase
* Auth0
* Passport.js

Testing:

* Mocha + Chai
* Jest + Enzyme
* Previous ones + Sinon

Time:

* moment.js or date-fns

*only use custom DB and auth for large projects. For all the others, use Firebase*

source: <https://www.robinwieruch.de/essential-react-libraries-framework/>

---

### Para aprender diversas coisas sobre JS

<https://medium.com/dev-bits/a-perfect-guide-for-cracking-a-javascript-interview-a-developers-perspective-23a5c0fa4d0d>

* Functions: <https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Functions>

--- 


### How to learn a framework

<https://www.robinwieruch.de/how-to-learn-framework/>

1. Faça um resumo das coisas para estudar e adicione outras se necessário
2. Estude e vá produzindo
3. Pegue um projeto que te motive
4. Gaste horas pensando e quebrando a cabeça com o projeto
5. Procure ajuda no Google, SO e Slack
6. Termine o projeto e pegue feedbacks
7. Se ainda estiver preso na análise paralisatória, implemente o mesmo projeto em outros frameworks e repita os itens de 3 a 6.

Resumindo: CONSUMA E PRODUZA!!!

---

### Git essential commands

<https://www.robinwieruch.de/git-essential-commands/>

---

### Installation

One can install react by using CDNs or node packages. There is another alternative, `create-react-app` which comes set with Babel.

---

### JSX

JSX produces React "elements"

`const element = <h1>Hello, JSX!</h1>;`

Quando o elemento tem children, colocá-los entre parênteses:

```
const element = (
	<div>
	  <h1>Hello!</h1>
	  <h2>Good to see you here.</h2>
	</div>
);
```

### Destructuring Assignment

`const { isSubmitted, buttonText } = this.attrs;`

is equal to:

```
const isSubmitted = this.attrs.isSubmitted;
const buttonText = this.attrs.buttonText;
```

---

### React components, elements and instances

"For a React component, props are the input, and an element tree is the output"

"Unless you need features available only in a class, we encourage you to use function components instead."

Element is a plain object containing what you want to see on screen.

Component takes props as input and element tree as output.

Props flows one way in React: from parent to children.

"An instance is what you refer to as `this` in the component class you write. It is useful for storing local state and reacting to the lifecycle events."

React takes care of creating instance for you for the class components you write.

---

### Variables

Prefer to use `const` over `let` as immutability is embraced in React ecosystem.

`var` gets hoisted into global context (as it become property of the window object) so it can throw an error when used with `const`.

`var` also can get be defined locally to an entire function regardless of block scope.

Pushing itens to array declared with const or changing value of object keys declared the same way is allowed.

`let` allows to declare variables that are limited in scope to the block, statement, or expression on which it is used (source: <https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/let>)

Temporal dead zone: Unlikely `var` that returns *undefined* until evaluation, `let` returns *ReferenceError*. 

---

### Data structures

Some types:

* Array
* List
* Record
* Union
* Tagged union
* Object

source: <https://en.wikipedia.org/wiki/Data_structure>

---

### Immutability

We can use *spread syntax* and *concat* to no mutate arrays and objects, respectivelly.

`...state.words` and

`Object.assign`

