# React Documentation

- prerequisities: HTML, CSS, Javascript

### [1. Introduction to React](https://youtu.be/fRXL0X2WSK4)

#### 1.1 What is React?

- React is a flexible, efficent JavaScript Library.
- It is developed by Facebook in 2013 for building user interface.

#### 1.1 Why React?

- It helps us to create reusable components (small and isloated pieces of code using html, css, js)
- Load fast
- Allows us to use external plugin
- Major brands like facebook, instragram, youtube, airbnb use react.js

### [2. Environment setup](https://youtu.be/4wjI8fh77GM)

### [3. First react app](https://youtu.be/2Ec3h0z51aI)

3.1 create and run react app

    // create react app command
    npx create-react-app appName

    // run react app command
    cd appName
    npm start

3.2 understand File structure

### [4. JSX and JS Expression](https://youtu.be/6-r6pBA4eUY)

- JSX stands for JavsScript XML which allows us to use write html inside javascript and vice versa
- An example is here

  ```js
  import React from "react";

  const todoTitle1 = "make react series";
  const todoBody1 =
    "I have to create a lot of videos for react series starting from a scratch";

  const todoTitle2 = "make REST API series";
  const todoBody2 =
    "I have already crated node.js, express.js, ejs and mongodb series. It is time for making a REST API series";

  const App = () => {
    return (
      <div>
        <h2>TO-DO App</h2>

        <div>
          <h3>{todoTitle1}</h3>
          <p>{todoBody1}</p>
        </div>

        <div>
          <h3>{todoTitle2}</h3>
          <p>{todoBody2}</p>
        </div>
      </div>
    );
  };

  export default App;
  ```
