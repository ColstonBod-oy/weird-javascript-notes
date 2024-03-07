<div id="top"></div>
<!--
*** Thanks for checking out the Best-README-Template. If you have a suggestion
*** that would make this better, please fork the repo and create a pull request
*** or simply open an issue with the tag "enhancement".
*** Don't forget to give the project a star!
*** Thanks again! Now go create something AMAZING! :D
-->



<!-- PROJECT SHIELDS -->
<!--
*** I'm using markdown "reference style" links for readability.
*** Reference links are enclosed in brackets [ ] instead of parentheses ( ).
*** See the bottom of this document for the declaration of the reference variables
*** for contributors-url, forks-url, etc. This is an optional, concise syntax you may use.
*** https://www.markdownguide.org/basic-syntax/#reference-style-links
-->



<!-- PROJECT LOGO -->
<br />
<div align="center">
  <a href="https://github.com/othneildrew/Best-README-Template">
    <img src="images/logo.png" alt="Logo" width="80" height="80">
  </a>

  <h3 align="center">Weird JavaScript Notes</h3>

  <p align="center">
    My lifelong notes about the weird 😵‍💫 and wild 🤪 features of JavaScript!
    <br />
    <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript"><strong>Explore the docs »</strong></a>
    <br />
    <br />
    <a href="https://reactjs.org/docs/getting-started.html">React JS Docs</a>
    ·
    <a href="https://html-css-js.com/js/">JavaScript Cheat Sheet</a>
    ·
    <a href="http://www.developer-cheatsheets.com/react">React Cheat Sheet</a>
    <br/>
    <br/>
    <a href="https://mail.google.com/mail/?view=cm&fs=1&to=bodoycolstond@gmail.com"><img alt="Gmail" src="https://img.shields.io/badge/Gmail-D14836?style=for-the-badge&logo=gmail&logoColor=white"/></a>&nbsp;
    <a href="https://www.facebook.com/colston.bodoy/"><img alt="Facebook" src="https://img.shields.io/badge/Facebook-%231877F2.svg?style=for-the-badge&logo=Facebook&logoColor=white"/></a>&nbsp;
    <a href="https://www.instagram.com/coldz.stone/"><img alt="Instagram" src="https://img.shields.io/badge/Instagram-%23E4405F.svg?style=for-the-badge&logo=Instagram&logoColor=white"/></a>&nbsp;
    <a href="https://twitter.com/OyColston"><img alt="Twitter" src="https://img.shields.io/badge/follow-%40OyColston-1DA1F2?logo=twitter&style=for-the-badge"/></a>
  </p>
</div>



<!-- TABLE OF CONTENTS -->
<details>
  <summary>📔 Table of Contents</summary>
  <ol>
    <li>
      <a href="#about-the-project">📄 About The Project</a>
      <details>
        <summary>1a</summary>
        <ul>
          <li><a href="#readme-template">📣README Template</a></li>
        </ul>
      </details>
    </li>
    <li>
      <a href="#decoupling-object-properties">📄 Decoupling Object Properties</a>
      <details>
        <summary>2a</summary>
        <ul>
          <li><a href="#2a-example">2a ▶️Example</a></li>
          <li><a href="#2a-application">2a 💡Application</a></li>
        </ul>
      </details>
    </li>
    <li>
      <a href="#immediately-invoked-function-expression">📄 Immediately Invoked Function Expression</a>
      <details>
        <summary>3a</summary>
        <ul>
          <li><a href="#3a-example">3a ▶️Example</a></li>
          <li><a href="#3a-application">3a 💡Application</a></li>
        </ul>
      </details>
      <details>
        <summary>3b</summary>
        <ul>
          <li><a href="#3b-example">3b ▶️Example</a></li>
          <li><a href="#3b-application">3b 💡Application</a></li>
        </ul>
      </details>
    </li>
  </ol>
</details>



<!-- ABOUT THE PROJECT -->
## About The Project

![Banner][react-logo]

&emsp;&emsp;&emsp;Hello! I'm Colston D. Bod-oy; I'm a React and Android developer, and I would be taking my 3rd year of college at the time that I made this repo. I'm an aspiring developer, and I would like to work for the big FAANG companies someday 😉.  
  
&emsp;&emsp;&emsp;I created this project so I could keep track of and recall things that I didn't know I could do in JavaScript, as I've just recently started learning it on a deeper level. I hope you'll find these notes useful! 😎.


### README Template

Btw, here's where I got this template. Also, don't forget to follow me on my social media links.

👉 [📒](https://github.com/othneildrew/Best-README-Template)

<p align="right">(<a href="#top">back to top ⤴️</a>)</p>



<!-- DECOUPLING OBJECT PROPERTIES -->
## Decoupling Object Properties 

&emsp;&emsp;&emsp;We could decouple object properties and use their values as properties of another object.

### 2a Example

&emsp;&emsp;&emsp;_Notice how we use the bracket notation instead of the dot notation for the last 2 properties of the cast object. It's because the decoupled values are not valid ```JavaScript``` identifiers (for example, a property name that has a space or a hyphen, or that starts with a number)._

  ```js
  const spells = {
    basic: "fire",
    special: "high voltage",
    ultimate: "💧",
  }

  const cast = {
    [spells.basic]: "🔥",
    [spells.special]: "⚡",
    [spells.ultimate]: "🌊",
  }

  console.log(cast.fire);            // 🔥
  console.log(cast["high voltage"]); // ⚡
  console.log(cast["💧"]);           // 🌊
  ```

### 2a Application

&emsp;&emsp;&emsp;_Below is a basic example of how we could use this feature when working with React's ```useReducer``` hook._

  ```js
  const initialState = {
    username: "",
    password: "",
  }
  
  export default function LoginForm() {
    const [state, dispatch] = useReducer((state, action) => {
      switch (action.type) {
        case "TEXT_FIELD":
          // Decoupling fieldType property from dispatch
          return { ...state, [action.fieldType]: action.payload }; 
        default:
          return state;
      }
    }, initialState);
    
    const { username, password } = state;
    
    return (
      <div className="App">
        <form className="form">
          <p>Please Login!</p>
          <input 
            type="text" 
            value={username} 
            onChange={(e) => 
              dispatch({ 
                type: "TEXT_FIELD", 
                fieldType: "username", 
                payload: e.currentTarget.value, 
              })
            }
          />
          <input 
            type="password" 
            value={password} 
            onChange={(e) => 
              dispatch({ 
                type: "TEXT_FIELD", 
                fieldType: "password", 
                payload: e.currentTarget.value, 
              })
            }
          />
        </form>
      </div>
    );
  }
  ```

<p align="right">(<a href="#top">back to top ⤴️</a>)</p>



<!-- IMMEDIATELY INVOKED FUNCTION EXPRESSION -->
## Immediately Invoked Function Expression 

&emsp;&emsp;&emsp;We can create and call a function expression at the same time.

### 3a Example

&emsp;&emsp;&emsp;_Notice the different ways we can create an ```IIFE```. For an ```IIFE``` to work, we first needed to change the context of the function keyword to be an expression, either by enclosing it inside parentheses or using operators. Note that the ```!``` operator will negate the returned boolean value of the ```IIFE```, and if the expression doesn't return anything, it will just result in true, while the ```+``` operator will try to add the returned value, but since it will always have no value on the left-hand side of the operator, no further actions will be executed._

  ```js
  var functionEx;
  (functionEx = function() {
    console.log("✔️")
  })(); // ✔️

  (function() {
    console.log("✔️")
  })(); // ✔️

  !function() {
    console.log("✔️")
  }(); // ✔️

  +function() {
    console.log("✔️")
  }(); // ✔️
  ```

### 3a Application

&emsp;&emsp;&emsp;_If your code doesn't support ```ES6```, you can't use the new ```let``` and ```const``` keywords for creating block-scoped local variables. You'll have to resort to the classic function scoping offered by ```IIFEs```._

  ```js
  {
    let part = "🦾";
    console.log(part); // 🦾
  }

  part; // ReferenceError: part is not defined

  (function() {
    var part = "🦾";
    console.log(part);
  })(); // 🦾

  part; // ReferenceError: part is not defined
  ```

<p align="right">(<a href="#top">back to top ⤴️</a>)</p>  

  
### 3b Example

&emsp;&emsp;&emsp;_```IIFEs``` can also be used to manage private data by returning functions that create closures for the local variables._

  ```js
  const robot = (function() {
    let part = "⚙️";
    return {
      getPart: () => part,
      setPart: (newPart) => part = newPart
    };
  })();

  console.log(robot.getPart()); // ⚙️
  robot.setPart("🤖");
  console.log(robot.getPart()); // 🤖
  ```
  
### 3b Practical Uses

&emsp;&emsp;&emsp;_Let's say you're using ```jQuery``` and another library that also assigns to the ```$``` global variable. We can resolve this naming conflict by wrapping the other piece of code with an ```IIFE``` that uses ```$``` as a parameter name. We can also do a similar thing if we want to capture the global object, no matter where we run our code. For example, the global object in the browser is window, while ```Node.js``` uses global. Aliasing variable names can also be used to optimize code so that it can be minified more efficiently. A ```JavaScript``` minifier like ```UglifyJS``` can shorten the function's parameter names to single-letter identifiers._

  ```js
  window.$ = function somethingElse() {
    // ...
  };

  (function($) {
    // ...
  })(jQuery);
  
  (function(global) {
    // ...
  })(this);
  
  (function(window, document, undefined) {
    // ...
  })(window, document);

  (function(w, d, u) {
    // ...
  })(window, document);
  ```

&emsp;&emsp;&emsp;_Not having the ```let``` keyword in ```ES6``` can also cause unexpected results when running asynchronous tasks inside a loop, as the value for ```i``` would immediately be changed until the loop condition wasn't fulfilled anymore. We can use ```IIFEs``` again in this case._

  ```js
  for (var i = 0; i < 3; i++) {
    setTimeout(() => console.log(`Current index: ${i}`), 100);
    // Current index: 3
    // Current index: 3
    // Current index: 3
  }

  for (var i = 0; i < 3; i++) {
    (function(index) {
      setTimeout(() => console.log(`Current index: ${index}`), 100);
    })(i);
    // Current index: 0
    // Current index: 1
    // Current index: 2
  }
  ```

<p align="right">(<a href="#top">back to top ⤴️</a>)</p>



<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->
[react-logo]: images/react-logo.png
