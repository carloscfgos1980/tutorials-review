## Todo app

# Location in Mac
/Users/carlosinfante/Desktop/coding-projects/winc-academy/frontend-course/MODULE9 - DEBUGGING and DOMAIN MODELING/REVIEW/react-hooks/useState/todo-app

# Location in GitHub
https://github.com/carloscfgos1980/React-useState-todo-app

# Goals:
- Change app from React class bassed component to React hook (use state)
- import the data from a local file (todosData).
- funtion to change the state of completed tasks (handleChange )
- Give a different style when the task is completed
- Cool css box shadow


1. All this shit of contructor, super, this state is decapicrated, instead is the useState like above.
2. The HandleChange function is way more simplier with hooks. Check example.
3. Render is not longer needed. Just return like above.

## TodoItems.js

The mapping is doing here isntead of doing in App.js like it was done with the original class-based todo-app. It could be also done in the App.js but this way is simplier.

# Steps:
1. App.js. Import the data:
import todosData from "./todosData"

2. App.js. Copy the imported data to a react variable:
const [todos, setTodos] = useState(todosData);

3. App.js Create a function to change the state of the completed tasks
    const handleChange = id => {
        let updatedTodos = todos.map(todo => {
            if (todo.id === id) {
                todo.completed = !todo.completed;
            }
            return todo;
        });
        setTodos(updatedTodos);
    };

4. Pass the data and the function to the TodoItems component
    return (
        <div className="todo-list">
            <TodoItems todos={todos} handleChange={handleChange} />
        </div>
    )

5. TodoItems.js. Create a function to apply certain style when the task is completed:
    const completedStyle = {
        fontStyle: "italic",
        color: "#cdcdcd",
        textDecoration: "line-through"
    }


6. TodoItems.js. Display the data
 
                {todos.map((todo) => (
                <div className="todo-items" key={todo.id}>
                    <input
                        type="checkbox"
                        checked={todo.completed}
                        onChange={() => handleChange(todo.id)}
                    />
                    <p style={todo.completed ? completedStyle : null}>{todo.text}</p>
                </div>
            ))}
6.1 Loop thru data (todos) and display the data in a input form.
                {todos.map((todo) => (
                <div className="todo-items" key={todo.id}>
                    <input
                        type="checkbox"
                        checked={todo.completed}
                    />
                    <p style={todo.completed ? completedStyle : null}>{todo.text}</p>
                </div>
            ))}

6.2  Attact onChange event to the input form:
onChange={() => handleChange(todo.id)}

6.3 Display the data with a turnary comparisson, so it will have a different style when is completed, using the funtion <completedStyle>:
 <p style={todo.completed ? completedStyle : null}>{todo.text}</p>


7. indes.css. Cool css style ussin shadowbox

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