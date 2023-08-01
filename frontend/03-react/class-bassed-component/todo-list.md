## Class based component app. Todo List

Location in Mac
/Users/carlosinfante/Desktop/coding-projects/winc-academy/frontend-course/MODULE9 - DEBUGGING and DOMAIN MODELING/REVIEW/react-class-based-components/todo-app


Location in GitHub
https://github.com/carloscfgos1980/React-classBased-todo-app

# Goals:
- Get the data from a different file (todosData). In this case this file start with small letters.
- Change the state (complete). Using deep copy.
- Apply specific style when the task is complete. Turnery comparisson (TodoItems.js lin 18)



App.js:
1.1 Import the data from a different .js file (todosData)
import todosData from "./todosData"

1.2 Passing this data to the initial state
        this.state = {
            todos: todosData
        }

1.3 Function to change the state (complete). Check out the deep coping (...todo,
                        completed: !todo.completed):
                  
   handleChange(id) {
        this.setState(prevState => {
            const updatedTodos = prevState.todos.map(todo => {
                if (todo.id === id) {
                    return {
                        ...todo,
                        completed: !todo.completed
                    }
                }
                return todo
            })
            return {
                todos: updatedTodos
            }
        })
    }

1.4 Looping through the initial state to pass the data and the function to <TodoItem> component
        const todoItems = this.state.todos.map(item => <TodoItem key={item.id} item={item} handleChange={this.handleChange} />


2. TodoItems.js. Display the text (item.text) in a list. 
2.1 create an object with css style.
    const completedStyle = {
        fontStyle: "italic",
        color: "#cdcdcd",
        textDecoration: "line-through"
    }

2.2 apply the function that handle the change of state (complete)
                onChange={() => props.handleChange(props.item.id)}

2.3 Turnery comparisson. If the task is complete, them apply the style that is in the object (completedStyle)
<p style={props.item.completed ? completedStyle : null}>{props.item.text}</p>

3. Cool css. Box shadow
index.css (lin 13 -24)
  box-shadow:
  /* The top layer shadow */
      0 1px 1px rgba(0,0,0,0.15),
          /* The second layer */
      0 10px 0 -5px #eee,
          /* The second layer shadow */
      0 10px 1px -4px rgba(0,0,0,0.15),
          /* The third layer */
      0 20px 0 -10px #eee,
          /* The third layer shadow */
      0 20px 1px -9px rgba(0,0,0,0.15);