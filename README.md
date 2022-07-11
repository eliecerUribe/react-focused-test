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
* Are negative margins legal and what do they do (margin: -20px)?
