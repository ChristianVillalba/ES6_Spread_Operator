# ES6_spread_operator
Created with [CodeSandbox](https://codesandbox.io/)  
Notes from: React module  
[The Complete 2021 Web Development Bootcamp](https://www.udemy.com/course/the-complete-web-development-bootcamp/)  
Instructor: Dr. Angela Yu 

## Description
This app is a Form consiting of: 
* A greeting heading "Hello"
* Input: First Name
* Input: Last Name
* Input: Email 
* Submit Button (deactivated)

The inputs provided by the user will be rendered and updated independently:
* The Heading will greet the user using the First Name and Last Name provided in the From.
* A new Paragraph will be rendered whe nthe user provides the input email in the From.

This form is the same as the one created in the repo [React: Complex State - Form Practice](https://github.com/ChristianVillalba/react_complex_state_form_practice.git)      
However, the code has been reduced using the Spread Operator:      
[Documentation: Spread Syntax](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_syntax)

---
## Notes

### Spread Operator (...)

Thanks to the ES6 **Spread Operator** we can simplify and reduce the amount of code.       
Spread syntax can be used when all elements from an object or array need to be included in a list of some kind.    

The ES6 Spread Operator is just three full stops ```...```     
And then I can add the name of the Array or Object that I want to expand into this position.

#### Arrays

eg: add the items in the Array ```citrus``` to the Array ```fruits```
```javascript
const citrus = ["lemon", "lime", "orange"];
const fruits = ["banana", "apple", "coconut", ...citrus]
```

It took this citrus array, expanded it (or spread it) into individual items       
and added each of those items into the position where I specified ```...citrus``` inside the array ```fruits```.     
We can change its position as any other item.

#### Objects

```javascript
const fullName = { fName: "James" , lName: "Bond" };
const user = { ...fullName , id: 007 , username: ShakenMartini }
```
We insert the ```...fullName``` into my ```user``` Object,       
This way ```user``` Object is going to be comprised of all of the elements inside the fullName Object (fName, lName),        
as well as any other ones already there (such as id and username).  
Using ```fullName``` (without Spread Operator ```...```) will nested the fullName Object inside user Object.

### Reducing our code: 

Thanks to the Spread Operator, our function:
```javascript
    setContact((prevValue) => {
      if (name === "fName") {
        return {
          fName: value,
          lName: prevValue.lName,
          email: prevValue.email
        };
      } else if (name === "lName") {
        return {
          fName: prevValue.fName,
          lName: value,
          email: prevValue.email
        };
      } else if (name === "email") {
        return {
          fName: prevValue.fName,
          lName: prevValue.lName,
          email: value
        };
      }
    });
```

... can be reduced to:

```javascript
    setContact((prevValue) => {
      return {
        ...prevValue,
        [name]: value
      };
    });
```
```[name]``` should be included between squared braces ```[]```     
We need to add the value that we want inside and an Array syntax.         
otherwise, it will be interpreted as if we want to create a new **key: value** pair where the **key** is the word **name**.     
How this works: [JavaScript set object key by variable (Stackoverflow) ](https://stackoverflow.com/questions/11508463/javascript-set-object-key-by-variable?noredirect=1&lq=1)  

...we could shorten this code even further because we only have one thing being returned:     
⚠ This syntax may be confusing.
```javascript
    setContact((prevValue) => ({ ...prevValue, [name]: value }));
```
We can delete ```return``` and its curly braces ```{}``` and semicolon ```;```     
And end up only with one object.      
We have to wrap it inside a set of parentheses ```()``` to remark that it's an Obj.   




---
## What I have learned with this project:
* Spread Operator
* Using the Spread Operator in
    * JS Arrays
    * JS Objects
* Reducing our code with the Spread Operator
