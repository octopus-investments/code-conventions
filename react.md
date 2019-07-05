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

- one component per file
- always define propTypes
- use class based components sparingly. Only for stateful components
- separate our dependency imports from local imports by a newline


#### 2.Structuring React component
- constructor (if needed)
- componentWillMount  [UNSAFE]
- componentDidMount
- componentWillReceiveProps [UNSAFE]
- shouldComponentUpdate (can only be used with declared React.PureComponent())
- componenetWillUpdate [UNSAFE]
- componenetDidUpdate
- click or event handler
- get methods (anything that’s required for rendering)
- render

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

- always use propTypes and defaultProps if needed

```jsx
// requires `transform-class-properties` to be installed on webpack
// http://babeljs.io/docs/plugins/transform-class-properties/
 
 
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
