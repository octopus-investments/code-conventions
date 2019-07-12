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

TODO: Do some reseasrch into stateless components

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
- when passing methods to subcomponents, we have to ensure that they have the right thiswhen they’re called (e.g. this.handleSubmit.bind(this))
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

#### 5.Passing setState() as a Function
- the dirty secret about setState — it’s actually asynchronous; that means you should not rely on the current state when calling setState — since you can’t be sure what that state will be!
- the solution — pass a function to setState, with the previous state as an argument.

```jsx
this.setState(prevState => ({ expanded: !prevState.expanded }))
```

#### 6.Props destructuring 
- Components with many props should have each prop on a newline, like above.
- suggestion: perhaps when we have more than 3 props, as then it becomes less read

```jsx
render() {
   const {
     model,
     title
   } = this.props
   return (
     <ExpandableForm
       onSubmit={this.handleSubmit}
       expanded={this.state.expanded}
       onExpand={this.handleExpand}>
       <div>
         <h1>{title}</h1>
         <input
           type="text"
           value={model.name}
           onChange={this.handleNameChange}
           placeholder="Your Name"/>
       </div>
     </ExpandableForm>
   )
 }
 ```
 
 - Avoid passing new closures to subcomponents, like so:
 
 ```jsx
 
<input
    type="text"
    value={model.name}
    // onChange={(e) => { model.name = e.target.value }}
    // ^ Not this. Use the below:
    onChange={this.handleChange}
    placeholder="Your Name"/>
```

#### 7.Functional Components
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

#### 8.Conditionals is JSX
- No, nested ternaries are not a good idea
- when we only want to render an element on one condition, instead of doing this

```jsx
{
 isTrue
  ? <p>True!</p>
  : <none/>
}
```

- use short-circuit evaluation

```jsx
{
 isTrue &&
   <p>True!</p>
}
```
