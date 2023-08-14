## Async Thunk Middleware. Todo-app Chris Blackely tutorial

Location in Mac:
/Users/carlosinfante/Desktop/coding-projects/winc-academy/frontend-course/MODULE9 - DEBUGGING and DOMAIN MODELING/REVIEW/redux/tutorials/3. API/Redux_API-Todo-chrisblakely

Location in GitHub:
https://github.com/carloscfgos1980/React-Redux-Toolkit-Todo_app-API-Middleware


export const getTodosAsync = createAsyncThunk(
    'todos/getTodosAsync',
    async () => {
        const response = await fetch('http://localhost:7000/todos');
        if (response.ok) {
            const todos = await response.json();
            return { todos }
        }
    }
);


    extraReducers: {
        [getTodosAsync.pending]: (state, action) => {
            console.log('fetching data....')
        },
        [getTodosAsync.fulfilled]: (state, action) => {
            console.log('fetched data successfully....')
            return action.payload.todos;
        },
    }

export const addTodoAsync = createAsyncThunk(
    'todos/addTodoAsync',
    async (payload) => {
        const resp = await fetch('http://localhost:7000/todos', {
            method: 'POST',
            headers: {
                'Content-Type': 'application/json',
            },
            body: JSON.stringify({ title: payload.title }),
        });

        if (resp.ok) {
            const todo = await resp.json();
            return { todo };
        }
    }
);

    extraReducers: {
        [addTodoAsync.fulfilled]: (state, action) => {
            state.push(action.payload.todo);
        },
    }


export const toggleCompleteAsync = createAsyncThunk(
    'todos/completeTodoAsync',
    async (payload) => {
        const resp = await fetch(`http://localhost:7000/todos/${payload.id}`, {
            method: 'PATCH',
            headers: {
                'Content-Type': 'application/json',
            },
            body: JSON.stringify({ completed: payload.completed }),
        });

        if (resp.ok) {
            const todo = await resp.json();
            return { todo };
        }
    }
);

    extraReducers: {
        [toggleCompleteAsync.fulfilled]: (state, action) => {
            const index = state.findIndex(
                (todo) => todo.id === action.payload.todo.id
            );
            state[index].completed = action.payload.todo.completed;
        },
    }

export const deleteTodoAsync = createAsyncThunk(
    'todos/deleteTodoAsync',
    async (payload) => {
        const resp = await fetch(`http://localhost:7000/todos/${payload.id}`, {
            method: 'DELETE',
        });

        if (resp.ok) {
            return { id: payload.id };
        }
    }
);

    extraReducers: {
        [deleteTodoAsync.fulfilled]: (state, action) => {
            return state.filter((todo) => todo.id !== action.payload.id);
        },
    }