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

There are function declarations and function expressions.

Hoisting only works with function declaration and not with function expression.

"A function defined in the global scope can access all variables defined in the global scope. A function defined inside another function can also access all variables defined in its parent function and any other variable to which the parent function has access."

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

---

### Rendering Elements

Elements are the small building blocks of React apps. And they describe what you want to see on the screen. React only updates what hasn't been modified.

### Hot module replacement (HMR)

* Statements will stay in developer console
* Can keep the application state after application reloads (e.g. Wizard or dialog with 3 screens can be remain opened because browser do not refresh page)

### Complex JavaScript in JSX

Map array method returns a new array.

"By assigning a key attribute to each list element, React can identify modified items when the list
changes. Make sure that the key attribute is a stable identifier."

"A good rule of thumb is that elements inside the map() call need keys."


### Components and props 

source: <https://reactjs.org/docs/components-and-props.html>

It's recommended naming props from the component’s own point of view rather than the context in which it is being used.

"All React components must act like pure functions with respect to their props."

### ES6 and arrow functions

Block body:

```
{list.map(item => {
	return (
    <div key={item.objectID}>
      <span>{item.author} is awarded {item.points} points</span>
    </div>
  );
})}
```

Concise body:

```
{list.map(item => 
  <div key={item.objectID}>
    <span>{item.author} is awarded {item.points} points</span>
  </div>
)}
```

"Two factors influenced the introduction of arrow functions: shorter functions and no existence of `this` keyword."

source: <https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions>

"As stated previously, arrow function expressions are best suited for non-method functions."

```
'use strict';

var obj = {
  i: 10,
  b: () => console.log(this.i, this),
  c: function() {
    console.log(this.i, this);
  }
}

obj.b(); // prints undefined, Window {...} (or the global object)
obj.c(); // prints 10, Object {...}
```

### ES6 Classes

React mixes the good parts of both programming paradigms (Functional programming and object-oriented programming).

"A class can also define functions. Because the function is associated with a class, it is called a method, or a class method."

Classes need to be instantiated.

When `extends` is used, that means that a class is inheriting some functionality from the other class. In React, when extending from Component, one functionality inherited is the `render()` method.


### Javascript fundamentals before learning React

Classes:

The instance of the class is represented by the `this` object within it, but ouside it is just assigned to a JavaScript variable.

The more specialized class inherites all the abilities from the more general class with the `extended` statement.

"The React component is only a React component because it inherits all the abilities from the React Component class which is imported from the React package."

App extends Component which grabs functionality as `this.setState()` from 'react' package.

"The only class you should extend from your React components should be the official React Component, because React favors composition over inheritance."

An example of Functional stateless react component:

```
const Gretting = (props) =>
  <h1>{props.greeting}</h1>
```

To see in the future (TF): All the conditional renderings in React

source: <https://www.robinwieruch.de/conditional-rendering-react/>

TF: High-order functions and components(source: <https://www.robinwieruch.de/gentle-introduction-higher-order-components/>). Basically, high order function is a function that returns a function.

Do not confuse rest (...) with destructuring ( { , } = )

That’s especially beneficial for functional stateless components, because they always receive the `props` object in their function signature.

```
// no destructuring
function Greeting(props) {
  return <h1>{props.greeting}</h1>;
}

// destructuring
function Greeting({ greeting }) {
  return <h1>{greeting}</h1>;
}
```

### ES6 Classes - MDN

One difference between class declaration and function declaration is that the first is not hoisted.

If there is a constructor present in the subclass, it needs to first call super() before using "this".

The use of super() is to call the super class (the upper class or parent class) methods and parameters.

---

### Basics in React

The ES6 class component uses a constructor to initialize local component state:

```
constructor(props) {
  super(props);
}
```

**It's mandatory to call super(props);** It makes possible to access `this.props` in the constructor. 

O state é amarrado na class usando objeto this, assim é possível acessar o estado local (local state) do componente todo.

No exemplo da lista, ao fazer o `this.state.list` a lista fica sendo parte do componente, no estado local dele. Assim, é possível adicionar, mudar ou remover itens da lista.

Toda vez que o estado do componente mudar, o método `render()` do componente vai rodar de novo. É assim que é possível mudar o estado local do componente e ver componente re-renderizar os dados corretos do estado local.

`this.props` contém os props que foram definidos por quem chamou o componente:

`<App name={user}` resulta em `this.props.name = user` 

Já o `state` contém dados específicos pelo component e podem mudar com o tempo. Ele é definido pelo usuário e deve ser um objeto Javascript simples.

Nunca mude o `this.state` diretamente. Trate ele como se fosse imutável.

### ES6 Object Initializer

It's a more concise way to initialize objects when the property name in the object is the same as the variable name.

### Unidirectional Data Flow

* Arrow functions tiram a necessidade de implementar 

`this.clickFunction = this.clickFunction.bind(this)`

pois elas já possuem o contexto do 'this' amarrado a elas. Dessa forma, fica assim:

```
const myFunction = () => {
 return this.props.a + this.props.b;
}


//The previous stated myFunction is the same as...
const myFunction = function() {
  return this.props.a + this.props.b;
}.bind(this);
```

Para definir um botão, o mesmo tem que ser codado em 3 lugares. Dentro do método `render()` utilizando a tag `<button>`, dentro do construtor, como `bind(this)` e fora do construtor como método da classe.

Fluxo de dados unidirecional pode ser resumido como: uma ação é iniciada na view layer com `onClick`, uma função ou método de classe modifica o componente de estado local (local component state) e então o método `render()` do componente roda novamente e faz o update da view.

### State and lifecycle in React

`this.state` serve para armazenar o estado inicial do Componente, enquanto que `this.setState` altera esse estado.

Primeiro, quando o componente é passado pra ReactDOM.render(), o construtor é chamado. Depois o método `render()`, depois o `componentDidMount()`.

Lembrar de usar setState() para modificar estado. Nunca modificar a variável diretamente.

O único lugar que se pode setar `this.state` é no construtor.

`this.props` e `this.state` podem ser atualizados de forma assíncrona e assim, não se deve depender deles pra gerar o próximo estado.

Exemplos:

```
// Wrong
this.setState({
  counter: this.state.counter + this.props.increment,
});
```

Para arrumar, usar uma segunda forma do setState() que aceita uma função em vez de um objeto. A função receberá o estado prévio como primeiro argumento e o props na hora que o update for aplicado como segundo argumento.

```
// Correct
this.setState((state, props) => ({
  counter: state.counter + props.increment
}));
```

Funções Arrow e regulares podem ser usadas.

As atualizações são mescladas (merged) da forma que um objeto não interfere no outro (o deixa intacto).

Os dados fluem pra baixo.

### Bindings

Se você quiser acessar `this.state` nos métodos de class, você tem que amarrar (bind) os métodos de classe no `this`.

Os métodos de classe não devem ser definidos dentro do constructor.

Usando ES6 Arrow Functions, os métodos de classe podem ser auto-vinculáveis (auto-bound):

```
class ExplainBindingsComponent extends Component {
  onClickMe = () => {
    console.log(this);
  }

  render() {
    return (
      <button
        onClick={this.onClickMe}
        type="button"
      >
        Click Me
      </button>
    );
  }
}
```

### Event Handler

Deve ser passada uma função para o Event Handler.

É preciso 'wrappear/amarrar' a propriedade ao ser passada ao método de classe. (High-order functions).

### Interactions with Forms and Events

"When using a handler in your element, you get access to the synthetic React event in your callback
function’s signature."

"We store the input value to the local state every time the value in the input field changes."

Uma função que retorna outra função é chamada de função de alta ordem (high-order function). Estas podem ser expressadas de forma mais concisa utilizando arrow functions.

Não há necessidade de passar a lista para o setState porque os merges em React são rasos, o que significa que ele mantém seus irmãos intactos (do this.state) quando executando o método this.setState para algum parâmetro individual.

### Forms - React Docs

When the value is read-only, it is an uncontrolled component in React.

TF: Estudar *computed property name* syntax. Eg:

```
// ES5
var partialState = {};
partialState[name] = value;
this.setState(partialState);
```

```
// ES6
this.setState({
  [name]: value
});
```

Use Formik to have a complete solution regard forms.

### Split Up Components

Props nada mais são que as propriedades da classe acima, que é extendida. Ex:

"Props, short for properties, have all the values passed to the components when we
used App component. That way, components can pass properties down the component tree."

### Composable Components

Foi usado o texto "Search" após o elemento <Search> para ilustrar como faz para um texto ficar visível para os children components. 

Isso ocorreu porque o texto "Search" estava dentro do elemento <Search> e por isso pode ser usado como children dele pelo valor this.props.children.

### Composition vs Inheritance - React Docs

É recomendável utilizar composição em vez de herança.

TF: Estudar melhor essa parte, principalmente a que uma variável é passada para as classes inferiores utilizando props.

Lembre-se que os componentes podem aceitar props arbitrárias, incluindo valores primitivos, elementos de React ou funções.

Se você quiser reusar funcionalidade que não seja de UI entre componentes, é sugerível extrair ela em um módulo separado de JavaScript. Os componentes podem então importar e utilizar essa função, objeto ou classe, sem precisar extendê-lo.

### Reusable Components

Facilita a criação de hierarquia entre os componentes, a fundação da camada view de React.

O componente <Button> espera que seja declarada uma propriedade className nos props.

### How to pass props to components in React - Robin blog

TF: React props destructuring.

Props são passadas apenas de cima pra baixo. Não tem como uma prop ser passada pro elemento pai.

Props são apenas de leitura, não há como em React setar props. Props são usadas para trafegar dados de um componente para outro em React, mas só de componentes pai para filhos.

`state` pode ser lido e escrito, enquanto `props` são apenas lidas.

state pode ser passado como props para os children components também.

Toda vez que o props ou state muda, o mecanismo de renderização do componente é acionado.

TF: Finalizar esse artigo, parei em "How to pass Props from child to parent Component?". source: <https://www.robinwieruch.de/react-pass-props-to-component/>

### Component Declarations

Lifecycle methods ou métodos de ciclo de vida aprendidos até agora: `constructor()` e `render()`

Functional stateless components (FSC): recebem props e retornam uma instância de componente em JSX. Não tem state, portanto, não podendo atualizar ou acessar o estado com `this.state` ou `this.setState()` (pois não tem o objeto *this*). Não possuem método de ciclo de vida com exceção do `render()` que é aplicado implicitamente em FSC.

O método constructor() roda apenas uma vez durante a vida do componente enquanto o render() roda uma vez no início e toda vez que o componente se atualiza.

React.createClass is deprecated as 15.5.

*ES6 destructuring in the function signature to destructure the props:*

```
function Search(props) {
  const { value, onChange, children } = props;
  return (
    <form>
      {children} <input
        type="text"
        value={value}
        onChange={onChange}
      />
    </form>
  );
}
```

é o equivalente a:

```
function Search({ value, onChange, children }) {
  return (
    <form>
      {children} <input
        type="text"
        value={value}
        onChange={onChange}
      />
    </form>
  );
}
```

que por sua vez equivale a:

```
const Search = ({ value, onChange, children }) =>
  <form>
    {children} <input 
      type="text"
      value={value}
      onChange={onChange}
    />
  </form>
```

### Styling Components

Pode-se passar objetos JavaScript para atributos de estilo de um elemento. Isso é chamado de *inline style*

Outras alternativas: styled-components, CSS Modules e Sass.

---

## Getting real with APIs

### Lifecycle methods

* constructor(props)

Chamado na inicialização. Pode-se chamar o state inicial do componente e fazer as vinculações (bind) com os métodos de classe.
 
* staticgetDerivedStateFromProps(props, state)

Chamado antes do `render()`, na montagem inicial e em updates subsequentes. Retorna um objeto para fazer o update do state ou null se não fizer nenhum update. Existe pra casos raros (quando o state depender das mudanças em props ao decorrer do tempo). É um método estático e não tem acesso à instância do componente.

* render()

É mandatório e retorna elementos como saído do componente. Deve ser puro, no sentido de não modificar o state do componente. Recebe props e state como entrada e retorna um elemento.

* componentDidMount()

É chamado uma única vez, quando o componente é montado. É a hora perfeita para fazer requisição assíncrona para buscar dados em uma API. Os dados buscados são armazenados no state local do component para serem mostrados no método `render()`. -Também serve para setar um timerID -

* shouldComponentUpdate(nexProps, nextState)

É sempre chamado quando o componente se atualiza em decorrência de mudanças no state ou props. Deverá ser utilizado em aplicações maduras para otimização de performance. Dependendo de um `boolean` retornado por esse método, o componente e seus childrens renderizarão ou não em uma atualização de ciclo de vida. Pode-se prevenir a renderização de ciclo de vida de um componente.

* getSnapshotBeforeUpdate(prevProps, prevState)

é invocado antes que o mais recente output renderizado é commited pro DOM. Em casos raros, o componente precisa de capturar informação do DOM antes de ser potencialmente modificado. Esse método possibilita isso de ser feito. O método `componentDidUpdate()` receberá qualquer valor retornado pelo método `getSnapshotBeforeUpdate()` como parâmetro.

* componentDidUpdate(prevProps, prevState, snapshot)

É utilizado sempre que uma atualização ocorrer, com a exceção da inicial. Pode ser usado pararealizar operações no DOM ou mais requisições assíncronas. Se seu componente utilizar o método `getSnapshotBeforeUpdate()` o valor que ele retorna será recebido como parâmetro `śnapshot`.

* componentWillUnmount()

É chamado antes de destruir o componente. Pode ser usado para tarefas de limpeza.

* componentDidCatch(error, info)

Introduzido em React 16, faz o catch de erros nos components e mostra uma mensagem de erro para o usuário.

### Lifecycle methods in React

Lifecycle methods podem ser sobrescritos (override) a fim de rodar código em tempos definidos durante o processo. Usar como referência o [lifecycle diagram](http://projects.wojtekmaj.pl/react-lifecycle-methods-diagram/)

render() pode retornar Arrays and fragments. E também portals.

Para interagir com o browser, utilizar "componentDidMount()" ou outros métodos de lifecycle. Manter "render()" puro. 

render() não será invocado se shoulComponentUpdate() retornar false.

"If you don’t initialize state and you don’t bind methods, you don’t need to implement a constructor for your React component."

Não usar "this.setState()" no Constructor. Utlizar nos outros métodos somente.

Não copiar props para dentro do state!

`forceUpdate()` pula o `shouldComponentUpdate()` e chama só o `render()`.

### State and Lifecycle

`componentDidMount` serve para setar um timerID e `componentWillUnmount()` para limpar o timerID.

Quando usar arrow functions, deve se omitir o `return`.

"Neither parent nor child components can know if a certain component is stateful or stateless, and they shouldn’t care whether it is defined as a function or a class.

This is why state is often called local or encapsulated. It is not accessible to any component other than the one that owns and sets it."

### Error Handling in React 16

Na maioria das vezes você vai setar um error boundary uma vez só e utilizar ela no aplicativo inteiro.

O EB só pega erros nos componentes abaixo deles na árvore.

Se um erro não for pego pelo EB, a árvore inteira de componentes é desmontada (unmounted).

### Fetching Data

source: <https://www.robinwieruch.de/react-fetching-data/>

### ES6 Spread Operators

source: <https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_syntax>

### Conditional Rendering

"In React a component has always to return an element or null."

TF: Pesquisar e estudar mais sobre "switch case operator in React with PropTypes."

Usar enums para substituir switchs em React.

High Order Components são bem úteis para conditional rendering em React.

Resumo de uso de casos:

* if-else
  * is the most basic conditional rendering
  * beginner friendly
  * use if to opt-out early from a render method by returning null
* ternary operator
  * use it over an if-else statement
  * it is more concise than if-else
* logical && operator
  * use it when one side of the ternary operation would return null
  * but be careful that you don’t run into bugs when using multiple conditions
* switch case
  * verbose
  * can only be inlined with self invoking function
  * avoid it, use enums instead
* enums
  * perfect to map different states
  * perfect to map more than one condition
* multi-level/nested conditional renderings
  * avoid them for the sake of readability
  * split up components into more lightweight components with their own simple conditional rendering
  * use HOCs
* HOCs
  * use them to shield away conditional rendering
  * components can focus on their main purpose
* external templating components
  * avoid them and be comfortable with JSX and JavaScript

source: <https://www.robinwieruch.de/conditional-rendering-react/>

Escolher o método condicional que seja mais adequado para você e sua equipe!

source: <https://reactjs.org/docs/conditional-rendering.html>

---

Codecademy: Para acessar conteúdo de forms:

```
const login = (
  <form action="#" onSubmit={this.authorize}>
    <input type="password" placeholder="Password"/>
    <input type="submit"/>
  </form>
);
```

```
authorize(e) {
  const password = e.target.querySelector('input type="password"]').value; 
  const auth = password == this.state.password;
  this.setState({
    authorized: auth
  });
}
```

Referência: Authorization Form

---

### Client- or Server-side Search

Aprendi como fazer consultas de API utilizando a busca e um botão, que, quando clicado, submita um evento que chama uma função e faz uma call para a API. O resultado é renderizado com `this.setState()`.

### Paginated Fetch

Aprendi a fazer busca paginada em que vários resultados a mais aparecem no fim da página, ao se apertar o botão "More".

### Client Cache

Parei na página 103.