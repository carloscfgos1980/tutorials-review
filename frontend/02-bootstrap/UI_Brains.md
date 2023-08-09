## React Bootstrap Crash Course 2022 | React JS UI Libraries | React Tutorial 2022
https://www.youtube.com/watch?v=0SIuH7yHCpA

# Goals:
- React Bootstrap Conceptual explanation of React Bootstrap, Installation and basic concepts
- NavBar
- Counter functionality. useState. min 25
- Form. min 28
- Color picker in google to get a specific color. min 33
- useState. Deep copy
- Table. Display List from bootstrap. min 38
- Axios. Use a Fake REST API
- Condictional rendering for the table

* Bootstrap is a rebuilt for React. The most popular framework.

* This tutorial has two parts:
1. Conceptual explanation of React Bootstrap, Installation and basic concepts
2. Applying those concepts in a Count app

# PART I
Location in Mac:
/Users/carlosinfante/Desktop/coding-projects/winc-academy/frontend-course/MODULE9 - DEBUGGING and DOMAIN MODELING/REVIEW/Bootstrap/React-bootstrap-UiBrains(I)

Location in GitHub:
https://github.com/carloscfgos1980/React-bootstrap-UI_library_I

# Steps:
1.1 npm install
In case that the React app is already created

1.2 npm start

1.3 npm install react-bootstrap bootstrap
* Always check the offitial websit for updates:
https://react-bootstrap.netlify.app

1.4 Index.js. Import React bootstrap:
import '../node_modules/react-bootstrap/dist/react-bootstrap';
import '../node_modules/bootstrap/dist/css/bootstrap.css';

1.5 Buttons.js. Buttons
5.1 Got to React and coppy the code for the button we want.
5.2 Copy in the place we want to use. In This case I created a component for the buttons (Buttonss.js) and then imported in App.js

1.6 Same example applies to Accordions, Nav Bar and Alerts

* Pretty simly and straight forward. This part ends in min 16 of the tutorial

--------------------------------------------------------

# Part II. 
Location in Mac:
/Users/carlosinfante/Desktop/coding-projects/winc-academy/frontend-course/MODULE9 - DEBUGGING and DOMAIN MODELING/REVIEW/Bootstrap/React-bootstrap-UiBrains(II)

Location in GitHub:
https://github.com/carloscfgos1980/React-bootstrap-UI_library_II

# 4 main elements in order to implement bootstrap:
1. Nav Bar
2. Counter. Card
3. Register. Card and form
4. UserList. table. Looping fthru fetched data using axios

# STEPS:
# 2.1 Create all the set for the app that we did before in part I.

2.2 NavBarComp.js. Create NavBar.
2.2.1 Create component (NavBarComp.js.)
2.2.1 Return the codes we copy from Bootstrap with the NavBar wwe want. In this example it is onle the NaVBar brand:
        <Navbar bg="dark" expand="sm" variant='dark'>
            <Container>
                <Navbar.Brand href="#home">React-Bootstrap</Navbar.Brand>
            </Container>
        </Navbar>
* It is important to apply variant='dark when the background is dark color and variant='light' when the background is light. This will adjust the colors so it is readable.


# 2.2 Create a counter:
2.2.1 Create a component for the counter (Counter.js)

2.2.2 Create a grid layout (respinsive): Container, Row, Col. 
In the coloum we specifif the width of the card that will show the data of the counter. In this case small screen, like this:
<Col xs={4}> // 4 represents the amount of colums. There is another way to do this with className.

2.2.3 Import the card inside <Col>

# 2.3 Register
2.3.1 Create component(Register.js)

2.3.2 Create the functionality. UseState. Explanation min 25 tutorial. 
2.3.2.1 useState. Instead of useing several useState. In this case is created a single React variable and inside this variable, we embed all the data we need:
    const [state, setState] = useState({
        user: {
            username: '',
            email: '',
            password: ''
        }
    });

2.3.2.2 Handle the state in the form with a single function. Using deep copy:
    const updateInput = (e) => {
        setState({
            ...state,
            user: {
                ...state.user,
                [e.target.name]: e.target.value
            }
        })
    }

2.3.2.3 Function to check that we are grabbing the values from the form, usually this is for dispatch the value to the store. In this case is only console.log
    const register = (e) => {
        e.preventDefault();
        console.log(state.user)
    }

2.3.3 Form:
2.4.3.1 In this case there are 3 input fields. They are all the same only for the typy of data (name and placeholder). name is the reac variable and placeholder is what is shown in the DOM. Every inputfield need a onChang event to catch the changes of the react variable. In this case he use a function that is the same for every input field. It could be just fire an annonymous function settting the state. 
                                <Form>
                                    <Form.Group className="mb-3">
                                        <Form.Control
                                            name="username"
                                            onChange={updateInput}
                                            className="mb-3" type='text' placeholder="Username" />
                                        <Form.Control

2.3.3.2 Attach onClick event to the button to submit the changes
                                        <Button
                                            onClick={register}
                                            variant="warning" type="submit">Register</Button>
                                    </Form.Group>

# 2.4 Table. min 38

2.4.1 Get to this website in order to use a fake REST API so we can fetch some data that will be display in the list
https://jsonplaceholder.typicode.com/users

2.4.2 Create a component (UserList.js)

2.4.3 Install Axios
npm install axios

2.4.4 Create service
- Create a Folder(service) inside src folder. 
- Create a file (UserService.js) inside service
UserService.js:
import axios from "axios";

export class UserService {
    static serverUrl = `https://jsonplaceholder.typicode.com/users`;

    static getAllUsers() {
        return axios.get(this.serverUrl);
    }
}



2.4.5 UserList.js. Call service from component

// Create the react variable
    let [state, setState] = useState({
        users: []
    });

// useEffect to fect the data. 
    useEffect(() => {
        UserService.getAllUsers().then((response) => {
            setState({
                ...state,
                users: response.data
            })
        }).catch((error) => {
            console.log(error);
        });
    }, [])
- UserService is the name of the componentwe create for the service
- UserService is the function used inside this component. it used <class> which is an element from backend (python)

2.4.6 Display the Lis as a Table. It is important the the table head has to match the table body in the amount and name of columns.
* Condictional rendering to make sure that nothing is shown f there is not data:

                                    state.users.length > 0 &&
                                    state.users.map(user => {