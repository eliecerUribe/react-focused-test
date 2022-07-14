# React focused test
I answer some questions about Javascript, CSS and React

### Javascript ###
* What is your favourite new javascript feature and why?

  Optional chaining because you can reduce the words you type when validating if a key exists in an object.

* Explain an interesting way in which you have used this javascript feature.
 For example: 
```javascript
    const person = { address : { postcode: 06710 } }
    
    // old way
    if (person && person.address && person.address.postcode) {}

    // with optional chaining
    if (person?.address?.postcode) {}
```

* Is there any difference between regular function syntax and the shorter arrow function syntax? (Write the answer in your own words)

  Arrow functions inherit the `this` variable from their parent context unlike regular functions that keep their own `this` within the scope it was defined.

* What is the difference between ‘myFunctionCall(++foo)’ and ‘myFunctionCall(foo++)’?

  For the first instance the value of `foo` is inscreased first and then it is evaluated.
  For the second instance `foo` is evaluated first then it is increased by one.

* In your own words, explain what a javascript ‘class’ is and how it differs from a function

  Javascripts classes is part of the OOP and it works based on entities defined as objects and the logic starts from that definition, from something macro.
Functions are orientend to mere functions as small parts of logic (micro) that can be reused for a bigger purpose.

### Css ###
* In your own words, explain css specificity.

  Css specificity refers to the priority that some selectors have to apply some rules to an element in the DOM.
  For example `id > class > direct reference of the element in the DOM (div, p, span)`
  
* In your own words, explain, what is ‘!important’ in css.  Also how does it work?  Are there any special circumstances when using it, where it’s behaviour might not be what you expect?

  `!important` can be used to break the css specificity and obligates with no restrictions to apply the property specified with `!important!`.
  
* What is your prefered layout system: inline-block, floating + clearing, flex, grid, other?  And why?

  Flex and I think because it's more fun and with a few props as `display`, `justify-content` and `align-items` you can create easily the main UI's layouts.
 
### Unit tests ###

* What technologies do you use to unit test your react components?

  I use `@testing-library/react`. Jest. Snapshots. 
  
* How do you test in your unit tests to see if the correct properties are being passed to child components.

  We can use the `objectContaining` or `toMatchObject` functions to validate the props is receiving a component. For example:
  
  ````javascript
  const expectedProps = {
    id: '123',
    name: "Client"
  };
  const result = rendererResult.root.findByType(Avatar);
  
  expect(result.props).objectContaining(expectedProps);
    ````
  ### React ###
  
  Create a react component that has a `<div/>` with a border.
  Inside this `<div/>` should be a `<span/>` that displays the ‘live’ width of the browser window at all times.  Keep in mind that the size of the window could easily be changed by the user and you should reflect this.
  
  ````javascript
  import React, { useState, useEffect } from "react";

  const myComponent = () => {
    const [width, setWidth] = useState(window.innerWidth);
    
    useEffect(() => {
      const handleResize = () => setWidth(window.innerWidth);
      window.addEventListener("resize", handleResize);
      
      return () => {
        window.removeEventListener("resize", handleResize);
      };
    }, []);
    
    return (<div><span>My window size {width}</span></div>)
  }
  ````
  
  Inside the `<div/>` you created in the previous step, add a text input that, as a number is entered into it, uses that number to set the height of the div itself in pixels, live as you update the text field (keypress not change event).
  
  ````javascript
  import React, { useState, useEffect } from "react";

  const MyComponent = () => {
    const [width, setWidth] = useState(window.innerWidth);
    const [divHeight, setDivHeight] = useState(0);
    
    const handleOnChange = (e) => {
      setDivHeight(e.target.value);
    }
    
    useEffect(() => {
      const handleResize = () => setWidth(window.innerWidth);
      window.addEventListener("resize", handleResize);
      
      return () => {
        window.removeEventListener("resize", handleResize);
      };
    }, []);
    
    return (
      <div style={{ height: `${divHeight}rem` }}>
        <span>My window size {width}</span>
        <input type="text" onChange={(e) => handleOnChange(e)} />
      </div>
    )
  }
  ````
  Add the following code to your project root (same project as in step 2, but add the code in the global / window space):  

  ````javascript
  let divHeight;
  window.setDivHeight = (height) => divHeight = height;
  ````

  Add a HOC for your div component that allows you to set the height of your <div/> component from the previous steps by calling that external function.
  
   ````javascript
  let divHeight = 0;
  window.setDivHeight = (height) => (divHeight = height);

  const MyCompnent = ({ setDivHeight }) => {
    const [width, setWidth] = useState(window.innerWidth);
    const [newDivHeight, setNewDivHeight] = useState();

    const handleOnChange = (e) => {
      setDivHeight(e.target.value);
      setNewDivHeight(divHeight);
    };

    useEffect(() => {
      const handleResize = () => setWidth(window.innerWidth);
      window.addEventListener("resize", handleResize);
      return () => {
        window.removeEventListener("resize", handleResize);
      };
    });

    return (
      <div style={{ height: `${newDivHeight}rem` }}>
        <span>My window size {width}</span>
        <input type="text" onChange={(e) => handleOnChange(e)} />
      </div>
    );
  };

  const withHighOrderComponent = (Component) => (props) => {
    return <Component setDivHeight={window.setDivHeight} {...props} />;
  };

  const WrappedComponent = withHighOrderComponent(MyCompnent);

  const App = () => {
    return <WrappedComponent />;
  };
  ````


   

   
