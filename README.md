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
        <li><a href="#example">Example</a></li>
        <li><a href="#practical-use">Practical Use</a></li>
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

### Example

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

### Practical Use

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
