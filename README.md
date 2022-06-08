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
[![GitHub][github-shield]][github-url]&ensp;
[![LinkedIn][linkedin-shield]][linkedin-url]&ensp;
[![Twitter][twitter-shield]][twitter-url]&ensp;
[![Facebook][facebook-shield]][facebook-url]&ensp;
[![Reddit][reddit-shield]][reddit-url]&ensp;



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
  </p>
</div>



<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#about-the-project">About The Project</a>
      <ul>
        <li><a href="#readme-template">README Template</a></li>
      </ul>
    </li>
    <li>
      <a href="#decoupling-object-properties">Decoupling Object Properties</a>
      <ul>
        <li><a href="#2a-examples">Examples</a></li>
        <li><a href="#2b-practical-uses">Practical Uses</a></li>
      </ul>
    </li>
    <li>
      <a href="#immediately-invoked-function-expression">Immediately Invoked Function Expression</a>
      <ul>
        <li><a href="#3a-examples">Examples</a></li>
        <li><a href="#3b-practical-uses">Practical Uses</a></li>
      </ul>
    </li>
  </ol>
</details>



<!-- ABOUT THE PROJECT -->
## About The Project

![Banner][react-logo]

Hello! my name is Colston D. Bod-oy, I'm a React developer and was currently taking my 2nd year of college on the time that I made this repo. I'm an aspiring developer and I would like to work for the big FAANG companies someday 😉.  
  
I created this project so I could keep track and recall things that I didn't know I could do in JavaScript as I've just recently started learning it, hope you'll find these notes useful! 😎.


### README Template

Here's where I got this template btw, also don't forget to follow me on my social media links.

👉 [📒](https://github.com/othneildrew/Best-README-Template)

<p align="right">(<a href="#top">back to top</a>)</p>



<!-- DECOUPLING OBJECT PROPERTIES -->
## Decoupling Object Properties 

We could decouple object properties and use their values as properties of another object.

### 2a Examples

_Notice how we use the bracket notation instead of the dot-notation for the last 2 properties of the cast object, it's because the decoupled values are not valid JavaScript identifiers (for example, a property name that has a space or a hyphen, or that starts with a number)._

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

### 2b Practical Uses

_Below is a basic example of how we could use this feature when working with React's useReducer hook._

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

<p align="right">(<a href="#top">back to top</a>)</p>



<!-- IMMEDIATELY INVOKED FUNCTION EXPRESSION -->
## Immediately Invoked Function Expression 

We can create and call a function expression at the same time.

### 3a Examples

_Notice the different ways we can create an IIFE. For an IIFE to work, we first needed to change the context of the function keyword to be an expression either by enclosing it inside parentheses or using operators. Note that the ! operator will negate the returned boolean value of the IIFE and if the expression doesn't return anything, it would just result to true, while the + operator will try to add the returned value but since it would always have no value on the left-hand side of the operator, no further actions would be executed._

  ```js
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

### 3b Practical Uses

_If your code doesn't support ES6, you can't use the new let and const keywords for creating block-scoped local variables. You'll have to resort to classic function scoping offered by IIFEs._

  ```js
  {
    let part = "🦾";
    console.log(part);
  }

  part; // ReferenceError: part is not defined

  (function() {
    var part = "🦾";
    console.log(part);
  })();

  part; // ReferenceError: part is not defined
  ```

_IIFEs can also be used to manage private data by returning functions that create closures for the local variables._

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
  


<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->
[github-shield]: https://img.shields.io/github/followers/ColstonBod-oy?style=social
[github-url]: https://github.com/ColstonBod-oy
[linkedin-shield]: https://img.shields.io/badge/Connections-151-blue?style=social&logo=linkedin
[linkedin-url]: https://www.linkedin.com/in/colston-bod-oy-60a7521a4/
[twitter-shield]: https://img.shields.io/twitter/follow/OyColston?style=social
[twitter-url]: https://twitter.com/OyColston
[facebook-shield]: https://img.shields.io/badge/Friends-512-blue?style=social&logo=facebook
[facebook-url]: https://www.facebook.com/colston.bodoy
[reddit-shield]: https://img.shields.io/reddit/user-karma/combined/Coldz-Stone?style=social
[reddit-url]: https://www.reddit.com/user/Coldz-Stone
[react-logo]: images/react-logo.png
