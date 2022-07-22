## Here are the steps

Step I: The createElement Function
Step II: The render Function
Step III: Concurrent Mode
Step IV: Fibers
Step V: Render and Commit Phases
Step VI: Reconciliation
Step VII: Function Components
Step VIII: Hooks



''' 
const element = <h1 title="greeting">Hello Moringa</h1>
const container = document.getElementById("root")
ReactDOM.render(element, container)
'''


Lets dig deep into details of the three lines of code above for react app.

=> The first one defines a React element. 
=> The next one gets a node from the DOM. 
=> The last one renders the React element into the container.


Lets understund line One

const element = React.createElement(
    "h1",
    { title: "greeting" },
    "Hello Moringa"
)
<!-- 
React.createElement creates an object from its arguments.
 So we can safely replace the function call with its output. 
-->

Lets convert the code above to Vanilla JavaScript

const element = {
    type: "h1",       ///the type is a string that tells us about the type of the DOM we are creating

    props: {         ///Props is another object that uses keys and values 
    title: "greeting",
    children: "Hello Moringa",   /// children in this case is a string but it can also have an array. elements use trees DS
  },
}



const container = document.getElementById("root")
ReactDOM.render(element, container) => //it will be converted to Vanilla js to below code

'''

const node = document.createElement(element.type)
node["title"] = element.props.title

'''
we create the nodes for children so we create a text nide since we take on the node as a string 

const text = document.createTextNode("")
text["nodeValue"] = element.props.children


node.appendChild(text)
container.appendChild(node)

'''
Finally, we append the textNode to the h1 and the h1 to the container.
'''

### below is the refactored code to vanilla js

const element = {
  type: "h1",
  props: {
    title: "foo",
    children: "Hello",
  },
}
​
const container = document.getElementById("root")
​
const node = document.createElement(element.type)
node["title"] = element.props.title
​
const text = document.createTextNode("")
text["nodeValue"] = element.props.children
​
node.appendChild(text)
container.appendChild(node)

