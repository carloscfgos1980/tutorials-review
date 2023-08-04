## The-Net-Ninja_React

# Location in Mac:
/Users/carlosinfante/Desktop/coding-projects/winc-academy/frontend-course/MODULE9 - DEBUGGING and DOMAIN MODELING/REVIEW/react-hooks/useState nd useEffect/The_Net_Ninja-blog-app

# Location in GitHub:
https://github.com/carloscfgos1980/React-useState-useEffect-blog

# INSTRUCTIONS TO START THE APP:
1. Create a react app. Type in Command Line Interface:
   npx create-react-app learning-react
   N: learning-react is just the name of the file that will contain our application.

2. Delete the file reportWebVitals.js inside the folder src

3. Inside index.js we need to delete Import reportWebVitals and delete reporWebVitals() at the button of the page.

4. Afther we download a GitHub repository for React, we have a missing files of npm. To get the npm folders we type:
   npm install

5. Import React is only necessary in index.js unless we are using an older version of nudes (program).

6. Shortcut to create div and className. Ex:
   Type:
   div.content

pres Tab
It creates a div with the className of content. This is possible cos we add in setting Emmet:
Item: javascript
Value: javascriptreact

7. Shortcut to Create a stateless react component. This is possible because we install a package in VSCode called: Simple React Snippets
   Type:
   sfc
   then press keyboard: Tab

8. Delete App.css file and also delete importe App.css from './App.css' code from the App.j file

------------------------------------------------------------------------------------------------

#       INDEX

 Lesson 14. UseEffect hook (basic)
- Conceptual explanation of useEffect.

# Lesson 15 - useEffect Dependencies
- Explanation of dependency inside useEffect.

# Lesson 16. Using JSON server:
- Create a Fake REST API 
- Explanation of endpoints (API):

# Lessson 17. Fetching Data with useEffect
- Explanation of fetching data using useEffect
- Explanation of condictional rendering:

# Lesson 18. Conditional Loading message
- Display a message (is pending...) before the components are mounted to the DOM
- setTimeout funtion. Using this function only to simulate extra time by fetching the data.

# Lesson 19. Handling Fetch error
- Grab the error, either from the static app while fetching or from the server

# Lesson 20. Making a custum hook (useEffect).
- Make the useFetch an independent component so we can use it in different place of our app

# Lesson # 21. The React Router
- Set up the The Router

# Lesson # 22. Exact Match Routes
- Create a new route for a new component
- Make home route an exact route so it wont mess with other routes

# Lesson 23. Router Links
- use <Link> instead of <a href>. This make the request a lot faster cos it does not need to go to the server, instead everything is handle in the browser

# Lesson # 24. useEffect Cleanup.
- Stop the fetching once we are in a different page.

# Lesson # 25. Route Parameters. 
- UseParagrams to click a item from the list and redirect to the component with the details of this specif item.
- Create a route to the component of the details item.
- CSS. Elimante the underline of the anchor tag.

# Lesoon 26. Reusing Custom Hooks
- Click on the list and redirect to a component that has the item details by fetching this specific item
- Display the value of this Item in the DOM. Also the pending message while is fetching and an error message in case the data cannot be fetched.

# Lesson 27. Controlled Inputs (forms).
- Forms: input, text area, select field.

# Lesson # 28. Submit Events. 
- Create a function to submit the data <handleSubmit>.
- Attatch submit function to the div form.

# Lesson 29 - Making a POST Request. 
- Post the data (Fetch)
- Condictional rendering for the buttons.

# Lesson #30 - Programmatic Redirects.
- useHistory to automatically redirect to a different page after post the info

# Lesson # 31 - Deleting Blogs
-  DELETE request (API) with useHistory inside the fect function so it will redirect to home page.

# Lesson 32 - 404 Pages & Next Steps.
- In case that there is the page, it will show a message and redirect to the homepage.

------------------------------------------------------

* Since I am using a local Rest API, I need to run it:
npx json-server --watch data/db.json --port 8000

# Lesson 14. UseEffect hook (basic)
https://www.youtube.com/watch?v=gv9ugDJ1ynU&list=PL4cUxeGkcC9gZD-Tvwfod2gaISzfRiP9d&index=15
# Goals:
- Conceptual explanation of useEffect.


# Lesson 15 - useEffect Dependencies
https://www.youtube.com/watch?v=jQc_bTFZ5_I&list=PL4cUxeGkcC9gZD-Tvwfod2gaISzfRiP9d&index=15
# Goals:
- Explanation of dependency inside useEffect.

useEffect(()=>{
    console.log(blogs)
}, []); // empty array so the useEffect runs only once. 
* We place variable inside the this dependency when we want the useEffect to run just when this data change.

# Lesson 16. Using JSON server:
https://www.youtube.com/watch?v=eao7ABGFUXs&list=PL4cUxeGkcC9gZD-Tvwfod2gaISzfRiP9d&index=16
# Goals:
- Create a Fake REST API 
- Explanation of endpoints (API):
  http://localhost:8000/blogs

4.  To practice the API we create a fake API Rest(Lesson # 16), like this:
    a-) Open a new Terminal
    b-) Type:

        npx json-server --watch data/db.json --port 8000

Note: data/db.jason is the neame of the folder and the name of the json file that we stora the fake API in our project

# Lessson 17. Fetching Data with useEffect
https://www.youtube.com/watch?v=qdCHEUaFhBk&list=PL4cUxeGkcC9gZD-Tvwfod2gaISzfRiP9d&index=18
# Goals:
- Explanation of fetching data using useEffect
- Explanation of condictional rendering:
{ blogs && <BlogList blogs={blogs} /> }

useEffect(()=>{
    fetch('http://localhost:8000/blogs')
    .then(res=>{
        return res.json();
    })
    .then(data=>{
        setBlogs(data)
    })
}, []);
* We need to apply condictional rendering while passing the data to the components so it wont crash the app. The reason is that it takes little time to fecth the data and when the app runs, the data is not there yet, by using the conditional rendering, so the thing on the right, will only be output if the thing on the left is true:
{ blogs && <BlogList blogs={blogs} /> }

# Lesson 18. Conditional Loading message
https://www.youtube.com/watch?v=qtheqr0jgIQ&list=PL4cUxeGkcC9gZD-Tvwfod2gaISzfRiP9d&index=18
# Goals:
- Display a message (is pending...) before the components are mounted to the DOM
- setTimeout funtion. Using this function only to simulate extra time by fetching the data.

# Steps:
18.1 Create a react variable for this porpuse and set the initial value <true>. useFetch.js:
 const [isPending, setIsPending] = useState(true);

18.2 setPending to false once the data is fetched. useFetch.js:
      .then(data => {
        setIsPending(false);
        setData(data);

18.3 setTimeout function. useFetch.js:
setTimeout(() => {
 //fectch function in here
}, 1000)  // second argument (1000) so the fetch function will fire after 1000 ms (1 sec)

# Lesson 19. Handling Fetch error
https://www.youtube.com/watch?v=DTBta08fXGU&list=PL4cUxeGkcC9gZD-Tvwfod2gaISzfRiP9d&index=19

# Goals:
- Grab the error, either from the static app while fetching or from the server

19.1 Create a ract variable to grab the error and the initial value to <null>
  const [error, setError] = useState(null);

19.2 Check if the response is not ok (200) then throw our own error. This is when the problem is that we wrote a fault end point.
        .then(res => {
        if (!res.ok) { // error coming back from server
          throw Error('could not fetch the data for that resource');
        } 
        return res.json();
      })

19.3 Set the error to null once the data is fetched
      .then(data => {
        setIsPending(false);
        setData(data);
        setError(null);
      })

19.4 Pass the value of the error to the variable we created for this porpuse
      .catch(err => {
          setIsPending(false);
          setError(err.message);
        }


# Lesson 20. Making a custum hook (useEffect). 
https://www.youtube.com/watch?v=Jl4q2cccwf0&list=PL4cUxeGkcC9gZD-Tvwfod2gaISzfRiP9d&index=20
* Very important to reuse the funtion in different places
# Goals:
- Make the useFetch an independent component so we can use it in different place of our app

# Steps:
20.1 useFetch.js. Create new component (useFetct). We can name as we want but it has to start with "use" because it is a <hook>

20.2 useFetch.js. Create a function (useFetch) and copy everything inside
const useFetch = (url) => {
// copy in here the whole funcion (useEffect) that we had in Home.js component
}

20.3 useFetch.js. inside, function <useFetch>, copy the react variable that were in Home.js:
  const [data, setData] = useState(null);
  const [isPending, setIsPending] = useState(true);
  const [error, setError] = useState(null);

20.4 useFetch.js. import hooks on the top of the component:
import { useState, useEffect } from 'react';

20.5 useFetch.js. Convert the "fetch end point" into a variable so we can pass this value when we call the custom hook from a different component.
const useFetch = (url) => {
    ...
    fetch(url)

}

20.6 useFetch.js. At the button of the function (useFetch), return an object and place the 3 values inside it:
return { data, isPending, error }

20.7 Home.js. Delete the useEffect, react variable related to useEffect and the imported hooks from this component

20.8 Home.js. Call the useFetch:
  const { error, isPending, data: blogs } = useFetch('http://localhost:8000/blogs')
- const { error, isPending, data: blogs }. Destructure the variables inside the function.
- data: blogs. Assign the name blogs to the data. Like this we can simply let the loop as it was (blogs.map...). We could leave as data and the change the name while passing to the component, like this
      { blogs && <BlogList blogs={data} /> }
- useFetch('http://localhost:8000/blogs'). Pass the end point as an argument. In the SongGaver, I will have two arguments, the second for the delete function so it will mount again the elements in the DOM... let[s see how it goes]

# Lesson # 21. The React Router
https://www.youtube.com/watch?v=aZGzwEjZrXc&list=PL4cUxeGkcC9gZD-Tvwfod2gaISzfRiP9d&index=21
* This is already outdated. In amet-website i' have the new version
# Goals:
- Set up the The Router

# Steps:
21.1 Install Router package
    We need to install a npm package by typing this in a new terminal:

        npm install react-router-dom@5

Note: @5 means version 5 but version 6 should be available soon

21.2 App.js. Import the Router like this:
import { BrowserRouter as Router, Route, Switch } from 'react-router-dom';

21.3 Surround the app:
 return (
    <Router>
    // all app elements here
    </Router>
  );

21.4 Create the route. The <NavBar> is about outside the <Switch> so it will be always show in the DOM
      <div className="App">
        <Navbar />
        <div className="content">
          <Switch>
            <Route exact path="/">
              <Home />
            </Route>
          </Switch>
        </div>
      </div>

# Lesson # 22. Exact Match Routes
https://www.youtube.com/watch?v=EmUa_tcSM-k&list=PL4cUxeGkcC9gZD-Tvwfod2gaISzfRiP9d&index=22
# Goals:
- Create a new route for a new component
- Make home route an exact route so it wont mess with other routes

# Steps:
22.1 Create a new component (Create.js)

22.2 App.js. Create a new route:
            <Route path="/create">
              <Create />
            </Route>

22.3 Adjust the Home route so we get the other routes:
            <Route exact path="/">
              <Home />



# Lesson 23. Router Links
https://www.youtube.com/watch?v=DO-pSysGItQ&list=PL4cUxeGkcC9gZD-Tvwfod2gaISzfRiP9d&index=23

* It makes the website much more faster cos it doesnt need to make a request to the server everytime we click a new page inside our website, instead the changes are displayed in the DOM. In order to do that we change <a> for <links> as the example in the lesson:

# Goals:
- use <Link> instead of <a href>. This make the request a lot faster cos it does not need to go to the server, instead everything is handle in the browser

# Steps:
23.1 NavBar.js. Import Link:
import { Link } from "react-router-dom";

23.2 Substitute <a href> for <Link>. Like this:
<Link to="/">Home</Link>

23.3 Style a button from the NavBar differently. Inline style. There is already an example of this
        <Link to="/create" style={{ 
          color: 'white', 
          backgroundColor: '#f1356d',
          borderRadius: '8px' 
        }}>New Blog</Link>

# Lesson # 24. useEffect Cleanup.
https://www.youtube.com/watch?v=aKOQtGLT-Yk&list=PL4cUxeGkcC9gZD-Tvwfod2gaISzfRiP9d&index=24
# Goals:
- Stop the fetching once we are in a different page.
 
24.1 useFetch.js. Create Abort controler inside useEffect, at the top
    const abortCont = new AbortController();

24.2 useFetch.js. Associate the Abort controler with the fetch
      fetch(url, { signal: abortCont.signal })

24.3 return an annonymous function to abort the fetch associated to that signal.
    return () => abortCont.abort();

24.4 Create a condiction (if) avoid throw an error if we created that error by canceling the fetching. Like this:
      .catch(err => {
        if (err.name === 'AbortError') {
          console.log('fetch aborted')
        } else {
          // auto catches network / connection error
          setIsPending(false);
          setError(err.message);
        }
      })
* This might be a boiler plate. I will try to use this customs hook with this abort function.


# Lesson # 25. Route Parameters. 
https://www.youtube.com/watch?v=t7VmF4WsLCo&list=PL4cUxeGkcC9gZD-Tvwfod2gaISzfRiP9d&index=25
* Somehting related to links. I need to study theis lesson again
# Goals:
- UseParagrams to click a item from the list and redirect to the component with the details of this specif item.
- Create a route to the component of the details item.
- CSS. Elimante the underline of the anchor tag.

# Steps:
25.1 Create component <BlogDetails.js>

25.2 App.js. Create a route for this component.
            <Route path="/blogs/:id">
              <BlogDetails />
            </Route>

25.3 BlogList.js. Surround the <h2> and <p> with a link to BlogDetails component but we pass the <id>so it will only show the specific item we are clicking:
          <Link to={`/blogs/${blog.id}`}> 
            <h2>{ blog.title }</h2>
            <p>Written by { blog.author }</p>
          </Link>
- /blogs/${blog.id}`. Using template string(``) which allows to use variables(${blog.id}). 
* </blog> is the route we created. <${blog.id}> is the value we grab from the route.

25.4 BlogDetails.js. Use the hook <useParagrams>. This grab parameters from the route (in this case <id>)
  const { id } = useParams();
  const { data: blog, error, isPending } = useFetch('http://localhost:8000/blogs/' + id);

25.5 index.css. Erase the underline in Link which is really anchor tag:
.blog-preview a{
  text-decoration: none;
}

# Lesoon 26. Reusing Custom Hooks
https://www.youtube.com/watch?v=c-5VXl8yPQA&list=PL4cUxeGkcC9gZD-Tvwfod2gaISzfRiP9d&index=26
# Goals:
- Click on the list and redirect to a component that has the item details by fetching this specific item
- Display the value of this Item in the DOM. Also the pending message while is fetching and an error message in case the data cannot be fetched.

# Steps:
26.1 BlogDetails.js. Import useFetch on the top:
import useFetch from "./useFetch";

26.2 BlogDetails.js. Call the function useFetch inside the function BlogDetails
  const { id } = useParams();
  const { data: blog, error, isPending } = useFetch('http://localhost:8000/blogs/' + id);

26.3 Return the values we get from the Fetch. In this case is an array of a single object so we don't need to loop thru the array. In Amet-web I do differently. I use hook <useParagrams> to gran the parameter and then I loop thru the array of painting data that I have storaged in the store:
  return (
    <div className="blog-details">
      { isPending && <div>Loading...</div> }
      { error && <div>{ error }</div> }
      { blog && (
        <article>
          <h2>{ blog.title }</h2>
          <p>Written by { blog.author }</p>
          <div>{ blog.body }</div>
          <button onClick={handleClick}>delete</button>
        </article>
      )}
    </div>

# Lesson 27. Controlled Inputs (forms).
https://www.youtube.com/watch?v=IkMND33x0qQ&list=PL4cUxeGkcC9gZD-Tvwfod2gaISzfRiP9d&index=27
# Goals:
- Forms: input, text area, select field.

# Steps:

27.1 Create.js. Create the react variables to handle the data from the form

  const [title, setTitle] = useState('');
  const [body, setBody] = useState('');
  const [author, setAuthor] = useState('mario');

27.2 Create.js. Form: text input
        <input
          type="text"
          required
          value={title}
          onChange={(e) => setTitle(e.target.value)}
        />

27.3 Create.js. Form: text area
        <textarea
          required
          value={body}
          onChange={(e) => setBody(e.target.value)}
        ></textarea>

27.4 Create.js. Form: select area
        <select
          value={author}
          onChange={(e) => setAuthor(e.target.value)}
        >
          <option value="mario">mario</option>
          <option value="yoshi">yoshi</option>
        </select>



# Lesson # 28. Submit Events. 
https://www.youtube.com/watch?v=pJiRj02PkJQ&list=PL4cUxeGkcC9gZD-Tvwfod2gaISzfRiP9d&index=28
# Goals:
- Create a function to submit the data <handleSubmit>.
- Attatch submit function to the div form

# Steps:

28.1 Create.js. Create a function to attatch to the form div as a onSubmit event. It could be also an onClick event attact to the <add blog> button.

  const handleSubmit = (e) => {
    e.preventDefault();
    const blog = { title, body, author };
  }
 28.2 Create.js. Inside the function <handleSubmit>. call a function to prevent the page to refresh automatically:
 e.preventDefault();

 28.3 Create.js. Inside the function <handleSubmit>. Create an object (blog). This is the data that will post (API). We don't need to give an id coz the REST API asign ids automatically :
     const blog = { title, body, author };

      <form onSubmit={handleSubmit}>

# Lesson 29 - Making a POST Request. 
https://www.youtube.com/watch?v=EcRFYF4B3IQ&list=PL4cUxeGkcC9gZD-Tvwfod2gaISzfRiP9d&index=29
# Goals:
- Post the data (Fetch)
- Condictional rendering for the buttons

# Steps:
29.1 Create.js. Create a react variable for pending state:
  const [isPending, setIsPending] = useState(false);

 29.2 Create.js. Inside the function <handleSubmit>. After the blog object. Set the pending to true
    setIsPending(true);

29.3 Create.js. POST Fetch function and then set the Pending to false (setIsPending(false))
    fetch('http://localhost:8000/blogs/', {
      method: 'POST',
      headers: { "Content-Type": "application/json" },
      body: JSON.stringify(blog)
    }).then(() => {
      setIsPending(false);
    })

29.4 Create.js. Create 2 buttons, one for is pending and another for actually add the data. He uses the rendering condiction but it would be shorter with comparisson ternary operators:

        {!isPending && <button>Add Blog</button>}
        {isPending && <button disabled>Adding Blog....</button>}

# Lesson #30 - Programmatic Redirects.
https://www.youtube.com/watch?v=TmVqwhBUiSM&list=PL4cUxeGkcC9gZD-Tvwfod2gaISzfRiP9d&index=30
# Goals:
- useHistory to automatically redirect to a different page after post the info

# Steps:
30.1 Create.js. Import the hook <useHistory>
import { useHistory } from "react-router-dom";

30.2 Create.js. Inside function <Create>, variable that contains the useHistory hook:
  const history = useHistory();

30.3 Create.js. Inside function <Create> and inside <fetch> function after send the data to post
.then(() => {
      setIsPending(false);
      // history.go(-1);
      history.push('/');
    })
- history.go(-1). This bring us an step behind.
- history.push('/'). This send us to the home page

# Lesson # 31 - Deleting Blogs
https://www.youtube.com/watch?v=Wb-0CkLiyQk&list=PL4cUxeGkcC9gZD-Tvwfod2gaISzfRiP9d&index=31
# Goals:
-  DELETE request (API) with useHistory inside the fect function so it will redirect to home page.

# Steps:

31.1 BlogDetails.js. Import useHistory

31.2 BlogDetails.js. Create a const to storage useHistory
  const history = useHistory();

31.3 BlogDetails.js. Create a function to delete the blog (item). 
  const handleClick = () => {
    fetch('http://localhost:8000/blogs/' + blog.id, {
      method: 'DELETE'
    }).then(() => {
      history.push('/');
    }) 
  }

31.4 BlogDetails.js. Place useHistory in order to redirect to the home page:
.then(() => {
      history.push('/');
    }) 

31.5 BlogDetails.js. Attach onClick event to <delete> button:
          <button onClick={handleClick}>delete</button>


# Lesson 32 - 404 Pages & Next Steps. 
https://www.youtube.com/watch?v=XW0t2lk4Ffo&list=PL4cUxeGkcC9gZD-Tvwfod2gaISzfRiP9d&index=32
# Goals:
- In case that there is the page, it will show a message and redirect to the homepage. 

# Steps:
32.1 Create a NotFound component

32.2 NotFound.js. return a text inform that something went wrong
  return (
    <div className="not-found">
      <h2>Sorry</h2>
      <p>That page cannot be found</p>
      <Link to="/">Back to the homepage...</Link>
    </div>
  );

32.3 NotFound.js. Link to home hage:
      <Link to="/">Back to the homepage...</Link>

32.4 App.js Create a new route with (*) that catch everything. It must be the last route
            <Route path="*">
              <NotFound />
            </Route>