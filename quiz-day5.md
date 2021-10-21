Questions
=========

#### 1) How do you access a function fetch() from a h1 element in JSX?

 
*       <h1>{fetch()}</h1>
    

  
*       <h1>${fetch()}</h1>
    

  
*       <h1>{fetch}</h1>
    

  
*       <h1>${fetch}</h1>
    

Check

* * *

#### 2) Which method in a React Component should you override to stop the component from updating?

 
*       willComponentUpdate
    

   
*       shouldComponentUpdate
    

  
*       componentDidUpdate
    

  
*       componentDidMount
    

Check

* * *

#### 3) What's used to pass data to a component from outside?

 
*       setState
    

 
*       render with arguments
    

  
*        PropTypes
    

  
*       props
    

Check

* * *

#### 4) Which method in a React Component is called after the component is rendered for the first time?

 
*       componentDidUpdate
    

  
*       componentDidMount
    

  
*       componentMounted
    

  
*       componentUpdated
    

Check

* * *

#### 5) Which of the following is correct syntax for a button click event handler, foo?


*       <button onclick={this.foo()}>
    

 
*       <button onclick={this.foo}>
    


*       <button onClick={this.foo()}>
    


*       <button onClick={this.foo}>
    

Check

* * *

#### 6) What happens when you call setState() inside render() method?


*       Repetitive output appears on the screen
    


*       Stack overflow error
    


*       Duplicate key error
    

 
*       Nothing happens. Life goes on!
    

Check

* * *

#### 7) What happens when the following render() method executes?

    
     render(){
       let langs = ["Ruby","ES6","Scala"]
         return (<div>
           {langs.map(it => <p>{it}</p>)}
         </div>)
     }
    


*       Displays the list of languages in the array
    

 
*       Error. Cannot use direct JavaScript code in JSX
    

 
*       Displays nothing
    

  
*       Error. Should be replaced with a for..loop for correct output
    

Check

* * *

#### 8) How do you write an inline style specifying the font-size:12px and color:red; in JSX

 
*       style={{font-size:12,color:'red'}}
    


*       style={{fontSize:'12px',color:'red'}}
    


*       style={fontSize:'12px',color:'red'}
    

 
*       style={{font-size:12px,color:'red'}}
    

Check

* * *

**Q1. What is Reconciliation?**

A. The process through which React deletes the DOM.

B. The process through which React updates and deletes the component.

C. It is a process to set the state.

D. The process through which React updates the DOM.

.

.

.

.

.

Ans: **D!!**

Explanation: Reconciliation is the process through which React updates the DOM. React use a “diffing” algorithm so that component updates are predictable and faster. React would first calculate the difference between the real DOM and the copy of DOM when there’s an update of components. Once it is finished calculating, the new update would be reflected on the real DOM.

**Q2. Which are the correct phases of component lifecycle?**

A. Mounting: `getDerivedStateFromProps()`; Updating: `componentWillUnmount()`; Unmounting: `shouldComponentUpdate()`

B. Mounting: `componentWillUnmount()`; Updating: `render()`; Unmounting: `setState()`

C. Mounting: `componentDidMount()`; Updating: `componentDidUpdate()`; Unmounting: `componentWillUnmount()`

D. Mounting: `constructor()`; Updating: `getDerivedStateFromProps()`; Unmounting: `render()`

.

.

.

.

.

Ans: **C!!!**

Explanation: It’s worth to mention that React internally has a concept of phases when applying changes to the DOM, including **Render**, **Pre-Commit** and **Commit**. `componentDidMount()`, `componentDidUpdate()`, `componentWillUnmount()` belongs to the “Commit” phase. Here’s an [interactive version](https://projects.wojtekmaj.pl/react-lifecycle-methods-diagram/), which shows each lifecycle method in each phase.

**Q3. Controlled Component vs Uncontrolled Component**

A. Controlled Components: every state mutation will have an associated handler function; Uncontrolled Components: store their own states internally

B. Controlled Components: store their own states internally; Uncontrolled Components: every state mutation will have an associated handler function

C. Controlled Components: A component who is so good at controlling itself; Uncontrolled Components: A component who has no idea how to control itself

D. Controlled Components: every state mutation does not have an associated handler function; Uncontrolled Components: does not store their own states internally

.

.

.

.

.

Ans: **A!!!**

Explanation: Just to clarify as the definition can be a bit tricky to understand. An example for controlled components:

handleChange(events) {  
  this.setState({ value: event.target.value.toUpperCase() })  
}

In this case, every value will be printed in uppercase letters, which is the `toUpperCase()`, an associated function handler.

An example for uncontrolled components (taken from React Doc):

class NameForm extends React.Component {  
  constructor(props) {  
    super(props);  
    this.handleSubmit = this.handleSubmit.bind(this);  
    this.input = React.createRef();    
  }  
  
  handleSubmit(event) {  
    alert('A name was submitted: ' + this.input.current.value);    event.preventDefault();  
  }  
  
  render() {  
    return (  
      <form onSubmit={this.handleSubmit}>  
        <label>  
          Name:  
          <input type="text" ref={this.input} />          
        </label>  
        <input type="submit" value="Submit" />  
      </form>  
    );  
  }  
}

In this case, the input of the value is stored in `ref` and can be used as a reference for the form.  
Though, React recommend to always use controlled component to implement forms, which is handled by a React component, while uncontrolled component is handled by the DOM.

**Q4. State vs Props**

A. Props is something that the parent doesn’t need and decide to throw around among other parents; State is the parent’s favorite child and something the component wants to nurture.

B. Props get passed to the component using naming conventions, like a function parameter; State is managed within the component and holds some information that may change over the lifetime of the component.

C. Props is a copy of real DOM; State is the definition of the real DOM.

D. Prop is managed within the component and holds some information that may change over the lifetime of the component; State gets passed to the component, like a function parameter

.

.

.

.

.

Ans: **B!!!**

Explanation: We can update state within the component using `setState()` , then we can pass the state to its children. Its children would use `this.props` to take whatever state from its parents.

Example:

// State.js <- pass the state "name" to Name.js  
class Form extends React.Component {  
  state = {  
    name = 'Megan';  
  }  
    
  render() {  
    <Name name={this.state.name} />  
}// Name.js <- it got the state "name" from State.js  
class Name extends React.Component {   
  render() {  
    <div>  
      <p>{this.props.name}</p>  
    </div>  
  }  
}

**Q5. What is the “key” prop?**

A. “Key” prop is just there to look pretty and there is no benefit whatsoever.

B. “Key” prop is a way for React to identify a newly added item in a list and compare during the “diffing” algorithm.

C. It is one of the attributes in HTML.

D. All I know is that it is NOT commonly used in array.

.

.

.

.

.

Ans. **B!!!**

Explanation: As stated in the answer, the reason we would get the the “missing key” warning because React needs the “key” prop to identify any new item in a list when re-rendering. It’s for the purpose of higher performance and efficiency. Here’s an [article](https://meganslo.medium.com/why-is-reacts-key-prop-important-b6bd51124270) I wrote which got into details of the purpose behind.
