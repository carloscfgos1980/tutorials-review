## The Net Ninja. Blog app

Location Mac
/Users/carlosinfante/Desktop/coding-projects/winc-academy/frontend-course/MODULE9 - DEBUGGING and DOMAIN MODELING/REVIEW/react-hooks/useState/NetNinja_blog-app

Location GitHub 
https://github.com/carloscfgos1980/React-useState-blog

# Lesson 01. Introduction
https://www.youtube.com/watch?v=j942wKiXFu8&list=PL4cUxeGkcC9gZD-Tvwfod2gaISzfRiP9d

# Goals:
- React concept
- React step up:
VSC:
- Simple React Snippets (auto complete)
- Use emmet. Explanation (min 4:45)

# Lesson 02. Creqting a React application
https://www.youtube.com/watch?v=kVeOpcw4GWY&list=PL4cUxeGkcC9gZD-Tvwfod2gaISzfRiP9d&index=2

# Goals:
- Create and Clean the app.

# Steps
npx create-react-app NetNinja_blog-app
code . // This open VSC in the corrent directory
index.js is responsible to mount all our components to the DOM
-Clean the app:
1. Delete reportWebVitals.js.
2. index.js:
- Delete import reportWebVitals and reportWebVitals()
3. Delete setupTest.js

# Lesson 03. Components & Templates
https://www.youtube.com/watch?v=9D1x7-2FmTA&list=PL4cUxeGkcC9gZD-Tvwfod2gaISzfRiP9d&index=3

# Goals
- Conceptual explanation of components.

# Lesson 04. Dynamic values in templates
https://www.youtube.com/watch?v=pnhO8UaCgxg&list=PL4cUxeGkcC9gZD-Tvwfod2gaISzfRiP9d&index=4

# Goals:
- Explanation of dymaic values. JavaScript can be written inside the function before the rutrn. To use javascript after return, we use {}.

# Lesson 05. Multiple components
https://www.youtube.com/watch?v=0sSYmRImgRY&list=PL4cUxeGkcC9gZD-Tvwfod2gaISzfRiP9d&index=5

- Goals:
Create NavBar and Home component. Very simple

# Lesson 06. Adding styles
https://www.youtube.com/watch?v=NbTrGcz4DW8&list=PL4cUxeGkcC9gZD-Tvwfod2gaISzfRiP9d&index=6
* All css in index.css. Delete app.css. This will apply globally
- import an specig type of letter.
- Using <flex> to align items
- inline stying. Explanation 4:45 min. Ex
        <a href="/create" style={{ 
          color: 'white', 
          backgroundColor: '#f1356d',
          borderRadius: '8px' 
        }}>New Blog</a>
* For inline styling we use {{}}. First the dynamic value. The second is the object that contains the styling values.

# Lesson 07. Click events
https://www.youtube.com/watch?v=0XSDAup85SA&list=PL4cUxeGkcC9gZD-Tvwfod2gaISzfRiP9d&index=7

# Goals:
- Attach events to elements like buttons, for example.

* Explanation of ho to use onClick. min 2:20.
const handleClick = ()=>{
    console.log("hello")
}
const handleClickAgain = (name)=>{
    console.log("hello" + name)
}
<button onClick={handleClick}>Click me!</button>
* if we invoque the functiion <handleClick()>, then it will fire by itself and not when we click it, that is why it does not have ().
<button onClick={()=>handleClickAgain("Carlos")}>Click me!</button>
* This is the way to do when we need to pass a value

# Lesson 08. Use State (use hook)
https://www.youtube.com/watch?v=4pO-HcG2igk&list=PL4cUxeGkcC9gZD-Tvwfod2gaISzfRiP9d&index=8
# Goals:
- Create reactive variables. Ex:  
const [name, setName]=useState('Carlos') // useState('Carlos') as initial value
setName('Miguel') //This changes the vale of name.

# Lesson 09. Intro Dev Tools
https://www.youtube.com/watch?v=rb1GWqCJid4&list=PL4cUxeGkcC9gZD-Tvwfod2gaISzfRiP9d&index=9

# Lesson 10. Outputting list.
https://www.youtube.com/watch?v=tHjxSVaj_wY&list=PL4cUxeGkcC9gZD-Tvwfod2gaISzfRiP9d&index=10
# Goals:
- Output a list by looping (map) thru an array of objects.

10.1 app.js. Create the dynamic value which is an array with objects within:
  const [blogs, setBlogs] = useState([
    { title: 'My new website', body: 'lorem ipsum...', author: 'mario', id: 1 },
    { title: 'Welcome party!', body: 'lorem ipsum...', author: 'yoshi', id: 2 },
    { title: 'Web dev top tips', body: 'lorem ipsum...', author: 'mario', id: 3 }
  ])
10.2 Passing the values to BlogList component:
      <div className="home">
      <BlogList blogs={blogs}  />
    </div>

10.3 Loop thru the array of values and display it as <h2> and <p>
          {blogs.map(blog => (
        <div className="blog-preview" key={blog.id} >
          <h2>{ blog.title }</h2>
          <p>Written by { blog.author }</p>
        </div>
* it is very important to put the Key inside the div, otherwise it will crash the app. This inform the DOM the type of info.

10.4 css style: boxshadow. index.css:
.blog-preview:hover {
  box-shadow: 1px 3px 5px rgba(0,0,0,0.1);
}

# Lesson 11. Props
https://www.youtube.com/watch?v=PHaECbrKgs0&list=PL4cUxeGkcC9gZD-Tvwfod2gaISzfRiP9d&index=11
* Same as above.

# Lesson 12. Reusing components
https://www.youtube.com/watch?v=-YpnB-zlkPU&list=PL4cUxeGkcC9gZD-Tvwfod2gaISzfRiP9d&index=12
# Goals:
- Reusing components explanation.
- looping with filter method to return certin elements. Ex:
<BlogList blogs={blogs.filter(blog=>blog.author ==== 'mario')}  />

# Lesson 13. Functions as props
https://www.youtube.com/watch?v=CWEOYFzgOJs&list=PL4cUxeGkcC9gZD-Tvwfod2gaISzfRiP9d&index=13
# Goals:
- Create a filter out function in order to delete
- Passing the function as a props
- Attatch onClick funtion to the button. This <onClick> has an annonymous function that will take the item. id as a parameter.



13.1 Create delete function. Home.js:

  const handleDelete = (id) => {
    const newBlogs = blogs.filter(blog => blog.id !== id);
    setBlogs(newBlogs);
  }
* This will filter out the object that match the cliked target objetc

13.2 Passing the function as a prop. Home.js:
      <BlogList blogs={blogs} title="All Blogs" handleDelete={handleDelete} />

13.3 get the function as argument or parameter... BlogList.js
const BlogList = ({ blogs, title, handleDelete }) => {

13.4. Attach onClick event to the button and an anonimous callback function <handleDelete>
          <button onClick={() => handleDelete(blog.id)}>delete blog</button>
* with () we place the item.id (blog.id)
