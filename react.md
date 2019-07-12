# React code style

#### 1.Code structure
- Always use JSX syntax
- First declare and then export component at the end:

```jsx
class Foo extends Component {
  ...
}
export default Foo;
```

- always define propTypes
- if using array or object propTypes please use arrayOf or objectOf for more detail [read documentation](https://reactjs.org/docs/typechecking-with-proptypes.html)
- use class based components sparingly, only for stateful components
- separate our dependency imports from local imports by a newline


#### 2.Structuring React class component
Order of lifecycle hooks
- constructor (if needed)
- componentWillMount [UNSAFE]
- componentDidMount
- componentWillReceiveProps [UNSAFE]
- shouldComponentUpdate (can only be used with declared React.PureComponent())
- componentWillUpdate [UNSAFE]
- componentDidUpdate
- click or event handler
- get methods (anything that’s required for rendering)
- render

- If using proptypes for class components put them below the constructor using the `static` keyword, for function components but the after the closing brace.

```jsx 
 
class Layout extends Component {
  static propTypes = {
     model: PropTypes.shape({
        id: PropTypes.number
     }),
     title: string
   }
 
   static defaultProps = {
     model: {
        id: 0
     },
     title: 'Your Name'
   }
 ```

#### 3.Props
- updating to a [cleaner way](https://daveceddia.com/where-initialize-state-react/) of initializing state

```jsx
// requires `transform-class-properties` to be installed on webpack
// http://babeljs.io/docs/plugins/transform-class-properties/
 
class Login extends Component {
    state = {
        ref_code: "",
        email: "",
        dob_day: "",
        dob_month: "",
        dob_year: "",
        receive_marketing: null
    };
```

- start off creating a functional component then change to a class component only if you need to use state or lifecyclehooks (we will look into using react-testing-library in the future for going down the completely functional component route).

- always use propTypes and defaultProps if needed

```jsx
class Layout extends Component {
  static propTypes = {
     model: PropTypes.shape({
        id: PropTypes.number
     }),
     title: string
   }
 
   static defaultProps = {
     model: {
        id: 0
     },
     title: 'Your Name'
   }
```

#### 4.Methods
- ES6 arrow function approach makes this more simpler and cleaner (also, with arrow functions we avoid any unexpected behaviours, which are not necessarily handled automatically with other approaches)

```jsx

handleSubmit = (e) => {
   e.preventDefault()
   this.props.model.save()
 }
 
 handleNameChange = (e) => {
   this.props.model.changeName(e.target.value)
 }
 
 handleExpand = (e) => {
   e.preventDefault()
   this.setState({ expanded: !this.state.expanded })
 }
```

-  Do not use an arrow function inside the attribute of a jsx element. Instead make your function/method an arrow function and call that in the component attribute

```jsx

function = () => {
   ...
}

// BAD
<Component
   onClick={() => this.function()}
/>

// GOOD
<Component
  onClick={this.function}
/>
```

#### 5.Passing setState() as a Function
- In the scenario where you have multiple setState and you want the latest one to change with the previous updated state changed carry out the steps below
- the dirty secret about setState — it’s actually asynchronous; that means you should not rely on the current state when calling setState — since you can’t be sure what that state will be!
- the solution — pass a function to setState, with the previous state as an argument.

```jsx
this.setState(prevState => ({ expanded: !prevState.expanded }))
```
TODO: Link up documentation

#### 6.Functional Components
- These components have no state and no methods. They’re pure, and easy to reason about. Use them as often as possible.

```jsx
import React from "react";
import PropTypes from "prop-types";
 
 
function ErrorMsg(props) {
    return (
        <div className="mt-0-5rem fz-smler">
            <img
                className="error-stop"
                src="/static/img/global/stop.svg"
                alt="stop icon"
            />
            {props.text}
        </div>
    );
}
 
 
ErrorMsg.propTypes = {
    text: PropTypes.string,
    loginAttempts: PropTypes.number
};
 
ErrorMsg.defaultProps = {
    text: "",
    loginAttempts: 0
};
 
export default ErrorMsg;
```

#### 7.Conditionals is JSX
- when we only want to render an element on one condition, instead of doing this

```jsx
// BAD
{
 isTrue
  ? <p>True!</p>
  : <none/>
}
```

- use short-circuit evaluation

```jsx
// GOOD
{
 isTrue &&
   <p>True!</p>
}
```

- this only applies to if an if statement is not returning a string as it will return the string `false` if the condition is not met
