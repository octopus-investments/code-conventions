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
