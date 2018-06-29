## menu

### Lesson 0 - Object Elements

`React` uses `ES2015` Symbols to `"tag"` its element-objects.

It uses a magic number as fallback on older browsers.

`React` uses virtual `DOM` elements, which become real `DOM` elements on a render.

A virtual `DOM` element can be defined as a simple object literal.

Normally you would use the `React`.
`createElement()` to create an element.

This is what the return value of a `React`.
`createElement()` call could look like.

This special property will be checked by `React` to ensure this object
is a `React` element and not just some user data
`React.createElement()`  sets it for you

This will also be checked by `React`.

 We will be talking about references
later, but if you're not using them, this has to be set to null and not
undefined

This defines the HTML-tag

This defines the properties that get passed down into the element

In this example there is just a single text node as child
a `CSS` class

styles can be passed as object literals
`React` uses camelCase instead of dashed-case (like `CSS/D3` do)

event handlers can be added as properties, too
`React` uses synthetic events, which basically try to normalize browser behaviour

another element that doesn"t have much configuration
`React` needs a `DOM` element as render target

`ReactDOM`OM is responsible for inserting the element into the DOM

### Lesson 1 - Element Factory

`React.createElement()`  needs type, properties, children.
This is less verbose than using plain object literals,
it hides the $$type/Symbol and ref mentioned in lesson 0

The second argument is the property object and has to be null if empty

### Lesson 2 - `JSX`

Now we will use `JSX`, which needs to be converted to `JavaScript`.
For this we will use `Babel`. `Babel` is normally used to convert `ES2015` to `ES5`, but
it also can convert `JSX` to `ES5`. `Babel`s browser version uses text/babel script tags.

`JSX` is the idiomatic way of creating elements.
It's basically `XHTML` with `{}` for dynamic content
also class has to be called className

Is the same as

`JSX` shines especially with simple elements that make up the majority

Is the same as

As we can see, everything else works as before

### Lesson 3 - Nested Elements

Elements can be nested, which will result in nested `React.createElement()`reateElement calls
As you can imagine, writing this without `JSX` would be pretty tedious

they can also, like mentioned in lesson 2, contain `JavaScript` in `{}`

`JavaScript` insertion has the same syntax in attributes as in normal text or elements

this `JavaScript` can contain elements too
it is also possible to "spread" an object as properties

### Lesson 4 - Components

The main selling point of `React` is its component system
components are used to encapsulate elements and their behaviour
see them as a mix of controller and view of MVC

Here we use stand alone elements and some data

Here the elements are encapsuled in a simple component function
They have to start with a capital letter and
return exactly ONE root element with or without nested elements (before `React` 16)

Since `React` 16.0.0, components can return an array of elements as well
In doing so, no additional wrapper element is created.
One caveat is that, similarly to what we do when rendering an array,
we have to add a unique key to each element in the array
(we'll see more on this in the next lesson)

Since `React` 16.2.0, we can use special "wrapper" components called fragments
that behave the same (no extra wrapper element created)
but remove the need to explitly set keys (fragments do this under the hood)

a component function can be used like an element

this translates to a `React.createElement()`  call
the null indicates that no properties have been set

for reference a `React`-internal `<div>` tag

gets converted to

### Lesson 5 - Properties

Components, like elements, can use properties, too

Which also works with an object and the spread (...) operator

This allows components with dynamic content

If an array is used as "child node" each child needs a unique key-property

### Lesson 6 - Property Types

PropTypes were removed from `React` 16 and are now their own package

Components get created to encapsulate stuff that should be together in one
place and for reuse.
Reuse requires the user of the component to supply the correct properties so
we can define a type of each property and set defaults

Add the propTypes (function-)property to the component function
to let it validate its (element-)properties

`React` supplies us with a bunch of types, like string

Add defaultProps (function-)property to set the defaults
if nothing was provided by the user

This will show a warning in the console, because customData should be a string

This will use the defaults

### Lesson 7 - Property Example

Here's a more practical example of a component
it formats a date and returns a `<span>` containing that formatted string

Also a more sophisticated type check for the date property
The property is required, because there are no defaults set

We have to supply a date object and the component does the formatting

### Lesson 8 - Nested Components

Components, like elements, can be nested

for this, the children property is used inside the component

This component just wraps its children in an `<li>` element

This component wraps its children into an `<ul>` element

If the `<List>` is created without children it gets a default child

now we render two `<List>`s, without and with Items

### Lesson 9 - Component Classes

`React.createElement()`reateClass was removed from `React` 16 and is now its own package

Often a component needs to maintain some internal state
for example if there is an interaction involved
in this case a component function is not sufficient
the component function can only have properties and no state
we need a component class with a render function

used for type-checking of the properties
same as with the component function

this method sets default values for missing properties
it will be called by `React`
before the components gets mounted into the DOM

this method sets the initial state for the component
it will be called by `React`
before the components gets mounted into the DOM
if this method is missing, `this.state` will be undefined

The state can be any `JavaScript` value, often it is an object

this method handles all the clicks on the `<span>` element

setState() can be called with an object that contains the new state
normally this triggers a call of render(), but `React` can batch multiple
calls and defer the render() call (make the call asynchronous)
To prevent this, setState can take a callback instead

This can lead to unexpected behaviour, if we rely on `this.state` or
`this.props` for our calculations
`this.setState`({times: `this.state.times` + 1})

The callback version doesn't have this problem
The callback gets the right state and `props` at time of the update

this method will be called by `React`
after the component got mounted into the DOM
also every time `this.setState`() was called
it's like the component function from before
but without a `props` argument

using the prop given by the creator of this component
properties are now in `this.props` instead of the `props` argument

returning an element with a click-handler and the `props` and
state values. state is stored in `this.state`

creating some instances of the interactive stateful component class
one with default color
Everything works exactly like with the simpler component functions
The interface has not changed for the user of this component

### Lesson 10 - Example App

An example of a simple `React` app
It uses simple component functions for its stateless components
and a complex component class to handle the interactions

First we have the Task and TaskList
They get all their data/state through their properties
`<TaskList>`
  `<Task text="Do something"/>`
  `<Task text="Do nothing"/>`
`</TaskList>`

Task needs a text property

TaskList needs an array of Task in its children property

Print the first element bold

This component handles the input
It needs to be a class, because the `<input>` element is stateful

gets called when someone types into the `<input>` element

gets called when someone clicks the `<button>` element

call the function that was added into its onAdd property

clear the state so the input is empty again after an add

renders the elements every time someone types or adds

The app keeps track of the current tasks in its state

this callback will be inserted into the onAdd property of the `<TaskInput>` component

adding a new task

this forces the `<TodoApp>` component to render

create the list of `<Task>` components from the tasks array in the state

some simple styling
and adding the add handler to the `<TaskInput>` component

we can use components directly


### Lesson 11 - Lifecycle Methods

If we use component classes, our components inherit
a bunch of methods, which get called by `React` at specifics
times to allow us to get more control over our components
a few of them we already met in lesson 9
Here are a few new ones. Not all of them, but the most important ones

This method is for default prop values
it gets called before the `props` are given to our component
the "real" `props` override them if there are any

This method is called before a component got mounted to the DOM
it returns values that are used for `this.state` 

This method gets called right before the component is mounted
can be used to initialize some synchronous configuration, that should
be available before the component renders

This method will be called right after the component got mounted
it's a good place to start some asynchronous tasks.
For example on the first mount it shows a loading message
then componentDidMount is called and gets some server data.

We clean up the data and get new from somewhere

Initial data load

We simulate a server request every 4 seconds

This method will be called before the component gets removed from the DOM
a bit like a destructor. Here we can do some cleanup.

This method is called before a render when new `props` or state is available
it won"t be called on the first render or if `this.forceUpdate()` is used
it can be used if some state or prop changes don"t require a rerender

we want to render on every change, this is the default behaviour

### Lesson 12 - Component refactor

Refactoring is another thing that is nice with `React`
First we'll talk about refactoring one component into another
if you're lucky, you can just change the implementation of a component
and don't need to change anything at the call-site

We start with a component that renders records somehow

The component has a simple `props`-interface

Now we switch out the implementation with something more complicated

We keep the `props`-interface the same

We could also switch it with something more dynamic

We still keep the `props`-interface the same

Some data

As we can see the components can be used exactly the same
If we copy the implementation of ViewAfter into ViewBefore,
everything keeps working

### Lesson 13 - Element Refactor

Refactoring an element is a bit more tricky
First, casing of `JSX` determines whether a tag is an element or component
lower case means element
upper case means component

becomes

becomes

Second, `React` converts all events these elements trigger, to
synthetic events. This is often not a problem, they are simply events.
But you can't trigger your own.
So even if your `<Input>` component accepts an `onClick` callback as property
You can't call it with the same event as an `<input>` element would

One approach could be this.
We simply implement our own `onChange` caller
Here we create a number input that only calls `onChange` on number inputs
(non-numbers trigger an empty change)

we could try to modify the event to get our data in
but this could mess things up
instead we prevent this event from further actions

filter empty-changes

then we extract our data and give it to `onChange`

Here we see, that the new NumberInput has a different interface
it's `onChange` property implies that events will be received, but this isn't
the case. Also, even if we would want to call it like the original input,
we would need to use upper case, and wouldn't win anything

Other approaches include not using "default" prop names in the first place
onUpdate instead of `onChange`

It could also happen that a component uses onMouseDown to do something internal
and triggers an `onChange`, which could cause confusion
Often components deliver richer interactions than elements in the first place
so their prop methods can reflect that with the name

### Lesson 14 - References

Sometimes we need some state from an element or a component
or it has to be directly modified somehow. For
this case, we can tell `React` to create references.

First we tell `React` to render an input with a
ref callback, it will be called, when the `DOM` of the input element
is available

This callback is called when the input element was mounted into the DOM
and again, with null, when it was unmounted again
For elements the rendered `DOM` node will be stored
For components the instance of the component will be stored.

We save a reference to it for later use.

This callback is called when the button is clicked
and uses `this.nameInput` to read out the value of the input.

Since references are local to their component
they can be used as local IDs to get elements
and don't override each other when another
instance of the component is created

### Lesson 15 - Simple Integration

Most of the time we have to use third party libraries
in our applications. Here we integrate a simple one
for date handling and use it with `React`. It doesn"t
use the `DOM` so it can be integrated fairly easy.

Simple libraries that are called synchronous can used
directly in `JSX` with the help of `{}`, since they are
just function calls

Nothing exciting happening here, just calling the library
and displaying its return values. First with some
elements, then used inside of a component.

### Lesson 16 - Advanced Integration

Sometimes we need to integrate more complex
libraries. Libraries that want to use the
DOM directly or require asynchronous interaction.
In this example we use D3.js, a free InfoVis library.

Since D3 needs to interact directly with the `DOM` we
should use a component class, because it can store
references to its `DOM-elements`.

We simply render an empty canvas and tell `React` to
store its reference after the render

After the first render, we grab the reference
to the canvas element in the `DOM` and pass it
to the library
Here we also use some additional color configuration

We also have some fine-granular control over the re-render
With the use of this lifecylce method

Here we could tell our library the new data for `props`
or state, so it can update the `DOM` elements on its own

At the end we always return false so our render method
isn't called and the canvas element isn't replaced

This lifecycle method can be used to free resources
before the component will be removed from the DOM.
Our canvas will be removed for sure, but often there
is state for the library, other objects, listeners etc.
they could be stored on the component and should be
deleted to prevent memory leaks

Now we can use the library as a component
No need for global IDs, every instance has its own canvas
reference stored, also its own color property

Wrapping the library interaction into a function

An example from `h`ttp://bl.ocks.org/mbostock/1b64ec067fcfc51e7471d944f51f1611`
its realeased under the `GPL-V3`