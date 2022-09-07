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
- VSCode
- node.js

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
- react module has babbel inside of it that helps us to run jsx: html inside javascript
- Create App.js file and put the following code inside of App.js 
- 

  ```js
  import React from 'react';

    const todoTitle1 = 'make react series';
    const todoBody1 = 'I have to create a lot of videos for react series starting from a scratch';

    const todoTitle2 = 'make REST API series';
    const todoBody2 = 'I have already crated node.js, express.js, ejs and mongodb series. It is time for making a REST API series';

    function App() {
      return (
        <div>
          <div>
            <h2>todo title</h2>
            <p>todo desc</p>
          </div>
         </div>

      );
    }

    export default App;

  ```

### [5. Component](https://youtu.be/qgLZSNppJOU)

- create a folder named as components inside src folder
- create new component and place inside components folder
- there are 2 types of components: functional component and class component
- example of functional component is given below

  ```js
  import React from "react";

  const Todo = () => {
    return <div>Todo</div>;
  };

  export default Todo;
  ```

- example of class component is given below

  ```js
  import React, { Component } from "react";

  class Todo extends Component {
    render() {
      return <div>Todo</div>;
    }
  }

  export default Todo;
  ```
  
- todo project example. create a file "Todos" inside component folder and use this file from App.js
    ```js
        // Header.jsx
        import React from 'react';

        function Header() {
          return (
            <header>Todo App</header>
          );
        }

        export default Header;
        
        // Footer.jsx
        import React from 'react';

        function Footer() {
          return (
            <footer>
              <p>Copyright by &copy;Anisul Islam</p>
              <p>Developed with &hearts; Anisul Islam</p>
            </footer>
          );
        }

        export default Footer;


        // Todos.jsx
        import React from 'react';
        import Todo from './Todo';

        function Todos() {
          return (
            <div className="todos">
              <Todo />
            </div>
          );
        }

        export default Todos;
        
        // Todo.js
        import React from 'react';

        function Todo() {
          return (
            <div>
              <h2>todo title </h2>
              <p>todo desc </p>
            </div>
          );
        }

        export default Todo;

        // App.jsx
        import React from 'react';
        import Todos from './components/Todos';

        function App() {
          return (
            <div>
              <Header />
              <Todos />
              <Footer />
            </div>
          );
        }

        export default App;

    ```
  
### [6. Props and destructuring](https://youtu.be/GQx58yfYqxo)

- we can pass information to another component using props. Props is like a varibale or object.
- example

  ```js
  import React from "react";

  import "./App.css";
  import Todo from "./components/Todo";

  const todoTitle = "make react series";
  const App = () => {
    return (
      <div>
        <Todo todoTitle={todoTitle} todoBody="this is the description" />
      </div>
    );
  };

  export default App;
  ```

  ```js
  // create Todo.js inside components folder
  // without destructuring
  import React from "react";

  const Todo = (props) => {
    return (
      <div>
        <h3>{props.todoTitle}</h3>
        <p>{props.todoBody}</p>
      </div>
    );
  };

  export default Todo;
  ```

  ```js
  // with destructuring
  import React from "react";

  const Todo = (props) => {
    const { todoTitle, todoBody } = props;
    return (
      <div>
        <h3>{todoTitle}</h3>
        <p>{todoBody}</p>
      </div>
    );
  };

  export default Todo;
  ```

### [7. Mapping components](https://youtu.be/OwwmIzH7FzI)

- example

  ```js
  // App.js
  import React from "react";

  import "./App.css";
  import Todo from "./components/Todo";

  const todos = [
    {
      id: 1,
      title: "make react series",
      body: "I have to create a lot of videos for react series starting from a scratch",
    },
    {
      id: 2,
      title: "make rest api series",
      body: "I have to create a lot of videos for rest api before the end of February 2022",
    },
  ];

  const App = () => {
    return (
      <div>
        <h2>TO-DO App</h2>
        <Todo todos={todos} />
      </div>
    );
  };

  export default App;
  ```

  ```js
  // Todo.js
  import React from "react";

  const Todo = (props) => {
    const { todos } = props;
    return (
      <div>
        {todos.map((todo) => (
          <div key={todo.id}>
            <h3>{todo.title}</h3>
            <p>{todo.body}</p>
          </div>
        ))}
      </div>
    );
  };

  export default Todo;
  ```

  ```js
  // we can make the JSX of Todo.js more cleaner as shown below
  import React from "react";

  const Todo = (props) => {
    const { todos } = props;

    const todoElements = todos.map((todo) => (
      <div key={todo.id}>
        <h3>{todo.title}</h3>
        <p>{todo.body}</p>
      </div>
    ));

    return <div>{todoElements}</div>;
  };

  export default Todo;
  ```
  
### [8. CSS Styling](https://youtu.be/02YWKDxLpwk)

- Inline styling
  ```html
    <div style={{ width: "300px", backgroundColor: "pink" }}>
        Inline styling
      </div>
  ```
- CSS Stylesheet
- CSS module

  - create a file name such as fileName.module.css as shown below

    ```css
    footer {
      height: 5vh;
      background-color: bisque;
      display: flex;
      justify-content: center;
      align-items: center;
    }

    .copyright {
      font-size: 0.9rem;
    }
    ```

  - use it in from another file as shown below

    ```js
    import React from "react";

    import styles from "./footer.module.css";

    const Footer = () => {
      return (
        <footer>
          <p className={styles.copyright}>
            All rights reserved by Anisul Islam
          </p>
        </footer>
      );
    };

    export default Footer;
    ```

### [9. state, setState, event handler](https://youtu.be/9AtJ4dM2xOU)

- state is a js object for storing current situation of a component

- example

  ```js
  // App.js
  import React from "react";

  import Counter from "./components/Counter";

  const App = () => {
    return (
      <div>
        <Counter />
      </div>
    );
  };

  export default App;
  ```

  ```js
  // Counter.js
  import React, { Component } from "react";

  export default class Counter extends Component {
    constructor(props) {
      super(props);

      this.state = {
        count: 0,
      };
    }

    handleIncrement = () => {
      this.setState({
        count: this.state.count + 1,
      });
    };

    render() {
      return (
        <div>
          <h2>Counter: {this.state.count}</h2>
          <button onClick={this.handleIncrement}>+</button>
        </div>
      );
    }
  }
  ```

### [10. Conditional rendering](https://youtu.be/roSfZjXp5us)

- rendering components based on if-else, element variable, ternary, short circuit

- example

  ```js
  // App.js
  import React from "react";

  import Todos from "./components/Todos";

  const todos = [
    {
      id: 1,
      title: "make react series",
      body: "I have to create a lot of videos for react series starting from a scratch",
    },
    {
      id: 2,
      title: "make rest api series",
      body: "I have to create a lot of videos for rest api before the end of February 2022",
    },
  ];

  const App = () => {
    return (
      <div>
        <h2>TO-DO App</h2>
        <Todos todos={todos} />
      </div>
    );
  };

  export default App;
  ```

  ```js
  // Todo.js
  import React from "react";

  const Todo = (props) => {
    const { todos } = props;

    const todosElements = todos.map((todo) => (
      <div key={todo.id}>
        <h3>{todo.title}</h3>
        <p>{todo.body}</p>
      </div>
    ));

    return <div>{todosElements}</div>;
  };

  export default Todo;
  ```

  ```js
  // Todos.js
  import React from "react";
  import Todo from "./Todo";

  const Todos = (props) => {
    const { todos } = props;

    // if-else rendering
    if (todos.length > 0) {
      return <div>{<Todo todos={todos} />}</div>;
    } else {
      return <p>no todo</p>;
    }
  };

  export default Todos;
  ```

  ```js
  // Todos.js
  import React from "react";
  import Todo from "./Todo";

  const Todos = (props) => {
    const { todos } = props;

    // element varibale rendering
    let element;
    if (todos.length > 0) {
      element = <div>{<Todo todos={todos} />}</div>;
    } else {
      element = <p>no todo</p>;
    }

    return element;
  };

  export default Todos;
  ```

  ```js
  // Todos.js
  import React from "react";
  import Todo from "./Todo";

  const Todos = (props) => {
    const { todos } = props;

    return (
      // ternary rendering
      <div>{todos.length > 0 ? <Todo todos={todos} /> : <p>no todo</p>}</div>
    );
  };

  export default Todos;
  ```

  ```js
  import React from "react";
  import Todo from "./Todo";

  const Todos = (props) => {
    const { todos } = props;

    // short-circuit rendering
    return <div>{todos.length > 0 && <Todo todos={todos} />}</div>;
  };

  export default Todos;
  ```

### [11. useState Hooks](https://youtu.be/skUOiqcVurY)

- useState() hook helps us to track state in a functional component.

- example

  ```js
  // App.js
  import React from "react";

  import Counter from "./components/Counter";

  const App = () => {
    return (
      <div>
        <Counter />
      </div>
    );
  };

  export default App;
  ```

  ```js
  // Counter.js
  import React, { useState } from "react";

  function Counter() {
    const [count, setCount] = useState(0);
    const handleIncrement = () => {
      setCount(count + 1);
    };

    return (
      <div>
        <h2>Counter: {count}</h2>
        <button onClick={handleIncrement}>+</button>
      </div>
    );
  }

  export default Counter;
  ```

### [12. Form Controlled components](https://youtu.be/kvGNlTh3rNQ)

- example

  ```css
  /* new-todo.module.css */
  .container {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 80vh;
  }
  .card {
    box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
    transition: 0.3s;
    width: 40%;
    padding: 1rem;
  }

  .card:hover {
    box-shadow: 0 8px 16px 0 rgba(0, 0, 0, 0.2);
  }
  .form-field {
    margin: 1rem 0;
  }
  input,
  select,
  textarea {
    padding: 0.5rem;
    width: 100%;
  }

  input:focus,
  select:focus,
  textarea:focus {
    background-color: antiquewhite;
  }

  textarea {
    resize: none;
    height: 10rem;
  }

  button {
    border: none;
    border-radius: 0.5rem;
    padding: 0.5rem 2rem;
    background-color: rgb(245, 169, 5);
    text-transform: uppercase;
    transition: all 0.3s;
  }
  button:hover {
    transform: scale(1.1);
  }
  ```

  ```js
  // NewTodo.js
  import React, { useState } from "react";

  import styles from "./new-todo.module.css";

  const NewTodo = () => {
    const [todo, setTodo] = useState({
      title: "",
      level: "high",
      body: "",
    });

    const handleInputChange = (event) => {
      setTodo({ ...todo, [event.target.name]: event.target.value });
    };

    const handleSubmit = (event) => {
      event.preventDefault();
      console.log(todo);
      setTodo({
        title: "",
        level: "high",
        body: "",
      });
    };

    return (
      <div className={styles.container}>
        <div className={styles.card}>
          <h2>New Todo</h2>
          <form onSubmit={handleSubmit}>
            <div className={styles["form-field"]}>
              <label htmlFor="title">Title: </label>
              <input
                type="text"
                id="title"
                name="title"
                onChange={handleInputChange}
                value={todo.title}
                required
              />
            </div>
            <div className={styles["form-field"]}>
              <label htmlFor="level">Level of Importance: </label>
              <select
                name="level"
                id="level"
                onChange={handleInputChange}
                value={todo.level}
                required
              >
                <option value="high">high</option>
                <option value="medium">medium</option>
                <option value="low">low</option>
              </select>
            </div>
            <div className={styles["form-field"]}>
              <label htmlFor="body">Body: </label>
              <textarea
                id="body"
                name="body"
                onChange={handleInputChange}
                value={todo.body}
                required
              >
                {" "}
              </textarea>
            </div>
            <div className={styles["form-field"]}>
              <button>create todo</button>
            </div>
          </form>
        </div>
      </div>
    );
  };

  export default NewTodo;
  ```

### [13. data passing: child to parent component](https://youtu.be/xdW2uFA-SOg)

- Another practical example: https://youtu.be/h7yq5lfDZc8
- Example

  ```js
  // App.js
  ```

### [14. useEffect Hook]()

- Example 1

  ```js
  import React, { useEffect, useState } from "react";

  // Rule: Don’t call Hooks inside loops, conditions, or nested functions

  // The useEffect Hook allows to perform side effects (fetching data, timers, directly updating the DOM) in components.

  // useEffct = componentDidMount + componentDidUpdate + componentWillUnmount

  const UseEffectHook = () => {
    const [count, setCount] = useState(0);

    // useEffect(() => {
    //   //Runs on every render
    // });

    // useEffect(() => {
    //   //Runs only on the first render
    // }, []);

    // useEffect(() => {
    //   //Runs on the first render
    //   //And any time any dependency value changes
    // }, [prop, state]);

    //Runs on every render
    // useEffect(() => {
    //   console.log("useEffect: " + count);
    // });

    //Runs only on the first render
    // useEffect(() => {
    //   console.log(count);
    // }, []);

    //Runs on the first render and also when the dependecy value changes
    useEffect(() => {
      console.log(count);
    }, [count]);

    return (
      <div>
        <h1>Count: {count}</h1>
        <button
          onClick={() => {
            setCount((count) => count + 1);
          }}
        >
          +
        </button>
      </div>
    );
  };

  export default UseEffectHook;
  ```

  ```js
  // Another example
  import React, { useState, useEffect } from "react";

  const UseEffectExample = () => {
    const [count, setCount] = useState(0);
    const [loading, setIsLoading] = useState(false);

    useEffect(() => {
      console.log("useEffect");
      console.log("isLoading: " + loading);
    }, [count]);

    return (
      <div>
        {console.log("render")}
        <h2>Count: {count}</h2>
        <button
          onClick={() => {
            setCount((count) => count + 1);
          }}
        >
          +
        </button>
        <button
          onClick={() => {
            setIsLoading(!loading);
          }}
        >
          change loading
        </button>
      </div>
    );
  };

  export default UseEffectExample;
  ```

### [15. fatch data using useEffect Hook]()

- example

  ```js
  import React, { useEffect, useState } from "react";

  const UseEffectHook = () => {
    const [todos, setTodos] = useState(null);
    const [isLoading, setIsLoading] = useState(true);
    const [error, setError] = useState(null);

    useEffect(() => {
      fetch("https://jsonplaceholde.typicode.com/todos")
        .then((res) => {
          if (!res.ok) {
            throw Error("error while fetching the data");
          }
          return res.json();
        })
        .then((data) => {
          setTodos(data);
          setIsLoading(false);
          setError(null);
        })
        .catch((error) => {
          setIsLoading(false);
          setError(error.message);
        });
    }, []);

    const errorMessage = error && <p> {error} </p>;
    const loadingMessage = isLoading && "data is loading";

    const todosElement =
      todos &&
      todos.map((todo) => (
        <div key={todo.id}>
          <p>{todo.title}</p>
        </div>
      ));

    return (
      <div>
        {errorMessage}
        {loadingMessage}
        {todosElement}
      </div>
    );
  };

  export default UseEffectHook;
  ```

### [16. how to create custom hook]()

- example

  ```js
  import React, { useState, useEffect } from "react";

  const useFetch = (url) => {
    const [data, setData] = useState(null);
    const [isLoading, setIsLoading] = useState(true);
    const [error, setError] = useState(null);

    useEffect(() => {
      fetch(url)
        .then((res) => {
          if (!res.ok) {
            throw Error("fecthing is not successful");
          } else {
            return res.json();
          }
        })
        .then((data) => {
          setData(data);
          console.log(data);
          setIsLoading(false);
          setError(null);
        })
        .catch((error) => {
          setError(error.message);
          setIsLoading(false);
        });
    }, [url]);

    return { data, isLoading, error };
  };

  export default useFetch;
  ```
  
### [17. add font awesome icons]()

- steps

  ```js
     // Add SVG Core
    npm i --save @fortawesome/fontawesome-svg-core
    
    // add Free icons styles
    npm i --save @fortawesome/free-solid-svg-icons
    npm i --save @fortawesome/free-regular-svg-icons
    npm i --save @fortawesome/free-brands-svg-icons   
    
    // add the react component
    npm i --save @fortawesome/react-fontawesome@latest

    
    // usage
    import { FontAwesomeIcon } from '@fortawesome/react-fontawesome';
    import { faPlusCircle, faMinusCircle } from '@fortawesome/free-solid-svg-icons';
    import { faYoutube } from '@fortawesome/free-brands-svg-icons';
    
    <FontAwesomeIcon icon={faPlusCircle}></FontAwesomeIcon>
    
    // use className for styling icons

   ```
   
### [18. useRef hook]()

- example

  ```js

  ```

### [19. react routing](https://youtu.be/YeW84KZVVbE)

- [react-routing-project](https://github.com/anisul-Islam/react-routing-project)

### [20. react todo projects]()

- [react todo project](https://github.com/anisul-Islam/react-todo-project)


### [21. react memo]()
- It helps to avoid unnecessary components rendering
  ```js
       // App.js
       import React, { useState } from 'react';
        import Message from './components/Message';

        const App = () => {
          const [count, setCount] = useState(0);
          console.log('app rendering');
          return (
            <div>
              <h1>Welcome to Memo</h1>
              <h2>Count : {count}</h2>
              <button
                onClick={() => {
                  setCount((count) => count + 1);
                }}>
                Increment
              </button>
              <Message numberOfMessages={0} />
            </div>
          );
        };

        export default App;

    // Message.js
    import React, { memo } from 'react';
    import PropTypes from 'prop-types';
    const Message = (props) => {
      console.log('message rendering');
      return <div>Message {props.numberOfMessages}</div>;
    };

    Message.propTypes = {
      numberOfMessages: PropTypes.number
    };

    export default memo(Message);
  ```
### [22. useCallback Hook]()
- It helps to avoid unnecessary components rendering for defining callback methods
- only component will be rendered when some states or props change 
  ```js
       // App.js
       import React, { useState, useCallback, useMemo } from 'react';
        import Message from './components/Message';

        const App = () => {
          const [count, setCount] = useState(0);
          console.log('app component rendering');

          const handleDataFromMessage = useCallback((data) => {
            console.log(data);
          }, []);

          const numbers = useMemo(() => {
            let number = 0;
            for (let index = 0; index < 5000000000; index++) {
              number++;
            }
            return number;
          }, []);

          return (
            <div>
              <h2>{numbers}</h2>
              <h2>Count : {count}</h2>
              <button
                onClick={() => {
                  setCount((count) => count + 1);
                }}>
                Increment
              </button>
              <Message onHandleDataFromMessage={handleDataFromMessage} />
            </div>
          );
        };

        export default App;


    // Message.js
    import React from 'react';
    import PropTypes from 'prop-types';
    const Message = ({ onHandleDataFromMessage }) => {
      console.log('message component rendering');
      onHandleDataFromMessage('hello I am from message component');
      return <div>Message</div>;
    };

    Message.propTypes = {
      onHandleDataFromMessage: PropTypes.func
    };

    export default React.memo(Message);

  ```
