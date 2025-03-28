# Components

## Rendering
React follows a declarative approach to rendering components, which means that developers specify what a component should look like, and React takes care of rendering the component to the screen.

### Virtual DOM
The virtual DOM (Document Object Model) is an important aspect of how React works. It is a lightweight in-memory representation of the DOM, and it is used to optimize the rendering of components in a React application.
- Components are written as Javascript classes or functions that define a render method. The render method return a description of what the component should look like, using JSX syntax.
- When a component is rendered, React creates a virtual DOM (VDOM) representation of the component.
- React compares the VDOM representation of the component with the previous VDOM representation (if it exists). If there are differences between the two VDOMs, react calculates the minimum number of DOM updates needed to bring the actual DOM into line with the new VDOM.
React updates the actual DOM with the minimum number of DOM updates needed to reflect the changes in the VDOM. 

### Component Life Cycle
React components have a lifecycle consisting of three phases: Mounting, Updating, and Unmounting along with several "lifecycle methods" that you can override to run code at particular time in the process.
- A component mounts when it's added to the screen
- A component updates when it receives new props or state, usually in response to an interaction
- A component umounts when it's removed from the screen

#### Effect Life
An Effect lifecycle is different from a component lifecycle. 

TODO: Look into effect lifecycle events more.

### Lists and Keys
When you render lists in React, you can use the key prop to specify a unique key for each item. This key is used to identify which item to update when you want to update a specific item.

### Refs
Refs provide a way to access DOM nodes or React elements created in the render method.

In the typical React dataflow, props are the only way that parent components interact with their children. To modify a child, you re-render it with new props. However there are a few cases where you need to imperatively modify a child outside of the typical dataflow. The child to be modified could be an instance of a React component, or it could be a DOM element. For both of these cases, React provides an escape hatch.

When you want a component to "remember" some information, but you don't want that information to trigger new renders, you can use a ref.

Typically, you will use a ref when your component needs to "step outside" React and communicate with external APIs--often a browser API that won't impact the appearance of the component. Here are a few of these rare situations:
- Storing timeout IDs
- Storing and manipulating DOM elements
- Storing other objects that aren't necessary to calculate the JSX

Best practices for refs:
- Treat refs as an escape hatch. Refs are useful when you work with external systems or browser APIs.
- Don't read or write ref.current during rendering. If some information is needed during rendering, use state instead.

### Events
Handling events with React elements is very similar to handling events on DOM elements. The are some syntax differences:
- React events are name using camelCase, rather than lowercase.
- With JSX you pass a function as the event handler, rather that a string.

### Higher Order Components
A higher-order component (HOC) is an advanced technique in React for reusing component logic. HOCs are not part of the React API, per say. They are a pattern that emerges from React's compositional nature

Concretely, a higher-order component is a function that takes a component and returns a new component.

Higher-order components are not commonly used in modern React code. In order to reuse logic, React hooks are mainly used now.