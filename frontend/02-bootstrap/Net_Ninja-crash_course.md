## BOOTSTRAP TUTORIAL
* This is a HTML and plan Vanilla JavaScript project

# Location in Mac:
/Users/carlosinfante/Desktop/coding-projects/winc-academy/frontend-course/MODULE9 - DEBUGGING and DOMAIN MODELING/REVIEW/Bootstrap/bootstrap-The_Net_Ninja
* There are a bunch of lessons. This is the root file

# Location in GitHub:
https://github.com/carloscfgos1980/Bootstrap-JavaScript-NetNinja-tutorial

## Lesson 1. Intro and Set up
https://www.youtube.com/watch?v=O_9u1P5YjVc&list=PL4cUxeGkcC9joIM91nLzd_qaH_AimmdAR

# Goals:
- Conceptual definition of bootstrap

# Definition:
A. <bootstrap> is fronted, CSS & Javascript for making mobile-first, responsive websites
B. Includes pre-mades components like navBars, modals, tabs, tooltips, buttons, accordions, etc
C. Comes with a fully backed with a responsive, 12 column, CSS grid system for layouts
D. Easy to customize and also ensure browser compatibility 

# STEPS:
1.1 Create index.html.
   1.1 Change the title
   1.2 Create <h1> inside the body

1.2 Isntall last version of bootstrap.
   2.1 - Copy the npm version form this website:
   https://getbootstrap.com/docs/5.2/getting-started/download/

1.3 Copy the CDN link

1.4 index.html: Past the link on the HEAD (lin 8 - 12):
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.2.2/dist/css/bootstrap.min.css" rel="stylesheet"
        integrity="sha384-Zenh87qX5JnK2Jl0vWa8Ck2rdkQ2Bzep5IDxbcnCeuOxjzrPF/et3URy9Bv1WTRi" crossorigin="anonymous">

1.5 index.html. Cut the script src and paste it in the body, just after the <h1>
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.2.2/dist/js/bootstrap.bundle.min.js"
        integrity="sha384-OERcA2EqjJCMA+/3y+gxIOqMEjwtxJY7qPCqsdltbNJuaOe923+mo//f6V8Qbsw3"
        crossorigin="anonymous"></script>

N: We could also install the package in the terminal:
npm install bootstrap@5.2.2

1.6. Create a "assets" folder to include some images later on.
   I can get the images from the gitHub for this lesson.

## Lesson 2. Bootstrap 5 new features
https://www.youtube.com/watch?v=YQRmczOYIG0&list=PL4cUxeGkcC9joIM91nLzd_qaH_AimmdAR&index=2

## Lesson 3. Color and Typography
https://www.youtube.com/watch?v=iUCyU_U0J2E&list=PL4cUxeGkcC9joIM91nLzd_qaH_AimmdAR&index=3
# Goals:
- Text style: headings, display, lead & alignment, text decorarion & font weight, colors, background colors

# Steps
3.1 <!--  heading tags -->
* We can give am especific class to the header. Ex
     <h2 class="h3">this is an 2 with an h3 class</h2>
   It is a bit of boiler plate coz we can simple write like this:
     <h3>this is an h3</h3>

3.2 <!-- display headings -->
* Give the style of heading to an element. It doesnt have to be a heading <h1>. Ex:
   <h1 class="display-1">display 1 heading</h1>
   <p class="display-1">paragraph with display-1 class</p>

3.3 <!-- lead text & alignment -->
* is a little bit bigger than a paraph
   Ex:
  <p class="lead text-center">hello ninjas</p>
  <p class="lead text-end">hello ninjas</p>
  <p class="lead text-start">hello ninjas</p> // This one we do not need to apply text-start becasue it is like that by default

3.4 <!-- text decoration & font weight -->
  <p class="text-decoration-underline">this is underlined text</p>
  <p class="text-decoration-line-through">this is line-through text</p>
  <p class="fw-bold">this bold text</p>
  <small>this is small text</small>

3.5 <!-- text colours -->
* Bootstrap has a set of determined colors (primary, secundary, etc) that we can change later on. EX
  <p class="text-primary">theme primary colour</p>
  <p class="text-secondary">theme secondary colour</p>
  <p class="text-info">theme info colour</p>
  <p class="text-warning">theme warning colour</p>
  <p class="text-success">theme warning colour</p>
  <p class="text-danger">theme danger colour</p>
  <p class="text-muted">theme danger colour</p>

3.6 <!-- bg colors -->
  <p class="text-white bg-primary">white text on primary bg</p>
  <p class="text-white bg-secondary">white text on secondary bg</p>
  <p class="text-light bg-danger">white text on secondary bg</p>


## Bootstrap 5 Crash Course Tutorial #4 - Buttons & Button Groups

https://www.youtube.com/watch?v=ZZXGmoQ4PdI&list=PL4cUxeGkcC9joIM91nLzd_qaH_AimmdAR&index=4
# Goals:
- Buttons: basic, anchor tag, size, outline(hover)

4.1 <!-- basic buttons -->
<button class="btn btn-primary">primary button</button> <!-- auto lightens text -->

4.2 <!-- anchor tags as buttons -->
<a href="#" class="btn btn-success">success anchor tag</a>
N: The color of the letters will swith from white to black, depending the background color

4.3 <!-- button sizes -->
<button class="btn btn-sm btn-warning">small warning button</button>

4.4 <!-- outlined styles -->
<button class="btn btn-outline-primary">outlined button</button>
N: When we hover over the button it will change to the color we have chosen, in this case primary color which is blue.

4.5 <!-- button groups -->
  <div class="btn-group">
    <a href="#" class="btn btn-primary">button 1</a>
    <a href="#" class="btn btn-warning">button 2</a>
    <a href="#" class="btn btn-success">button 3</a>
  </div>
N: When we use a div to group the buttons, they dont have space in-between

## Lesson 5. Utility classes
https://www.youtube.com/watch?v=nCeHeA7IsvU&list=PL4cUxeGkcC9joIM91nLzd_qaH_AimmdAR&index=5

# Goals:
- Classes: margin, padding, borders, box shadow, font weight

5.1 <!-- margin & padding -->
  <div class="my-3 px-5 bg-primary">margin in y dir, padding in x dir</div>
  N: "my" means marging top and button. Y axis
        "px" means padding to the left and right. X Axis
  <div class="mt-3 mb-4 ps-5 pt-4 pe-2 pb-1 bg-primary">m & p for each direction</div>
  N: t => top. Ex "mt" means margin top
    b => botton. Ex: "mb" means margin botton
    s => start (left). Ex: "ps" means padding left
    e => end (right). Ex: "pe" means padding right

5.2 <!-- borders -->
  <div class="m-3 p-3 border-start border-danger border-5">thicker border</div>
  N: In the above example we apply margin, padding, color (danger) and a thick border to the left. If one to apply border everywhere we simply do "border" instead of "border-start". 
  <div class="m-3 p-3 rounded border border-5">rounded corners</div>
  <div class="m-3 p-3 rounded-pill border border-5">rounded corners</div>
  N: this is is very cool!

5.3 <!-- box shadow -->
<div class="m-3 p-3 shadow-sm">element with small shadow</div>
N: "sm" stands for small shadow

5.4<!-- font weight -->
  <p class="fst-italic fw-light">italic light text</p>
  N: "fst" - type of letter.
  "fw"- thickness of the letter

## Lesson 6 - Containers
https://www.youtube.com/watch?v=Y6q8R-9y6a0&list=PL4cUxeGkcC9joIM91nLzd_qaH_AimmdAR&index=6

# Goals:
- Containers: Customize the width of the content in our page and adjust it to different point view (type of devise)

6.1 normal container. It centers the paraph in a center column. We can see some side margin when the screen is larger than celphones
  <div class="container my-5">
    <h2>normal container</h2>

6.2 Fluid containers. Adjust the lines to the size of the screen dynamically.
  <div class="container-fluid my-5">
  <h2>fluid container</h2>

6.3. Large container. It centers the parrapg in a center column. We can see some side margin when the screen is larger screen (ipads).
  <div class="container-lg my-5">
    <h2>100% until lg screens, then container</h2>

6.4 Small container
  <div class="container-xl my-5">
    <h2>100% until xl screens, then container</h2>
        N: It centers the parrapg in a center column. We can see some side margin when the screen is extar larger screen (14")

## Lesson 07 - Grid Layout (part 1)
https://www.youtube.com/watch?v=irfbn103AzE&list=PL4cUxeGkcC9joIM91nLzd_qaH_AimmdAR&index=7

# Location in Mac:
/Users/carlosinfante/Desktop/coding-projects/winc-academy/frontend-course/MODULE9 - DEBUGGING and DOMAIN MODELING/REVIEW/Bootstrap/bootstrap-The_Net_Ninja
* There are a bunch of lessons. This is the root file

# Location in GitHub:
https://github.com/carloscfgos1980/Bootstrap-JavaScript-NetNinja-tutorial

# Goals:
- Grid layout. We use this to organize the content in the DOM.
* By default the screen is divided in 12 columns!

6.1 Basic grid.  Divide the columns equally (lin 5 -28). EX
  <div class="container-lg my-5">
    <h2>basic grid</h2>
    <div class="row">
      <div class="col">


6.2. Set the columns with different size. (lin 30 -43)
  <div class="container-lg my-5">
      <div class="col">
  <div class="container-lg my-5">
  <div class="row">
   <div class="col-6">
   <div class="col-3">
    <div class="col-3">

6.3 Responsive column widths (lin 45 -59). Small screen they look like columns and larger than small screen the look like rows:

<div class="container-lg my-5">
<div class="row gy-3">
N: here it changes to "gy-3" to specified the amount (3) of responsise columns
 <div class="col-sm-4 col-lg-6">
<div class="col-sm-4 col-lg-3">
<div class="col-sm-4 col-lg-3">
N: "sm-4" means that when is small screen(it will be divided in 3 columns with a with of 4)
"col-lg-6"
"col-lg-3"
"col-lg-3"
Then when it is a larger screen the first column will ocupied 50% of the screen (6 columns) and the other 2 columns, 25% each one!

6.4 justifying column. 
  <div class="container-lg my-5">
    <h2>justifying columns</h2>
    <div class="row justify-content-center">
      <!-- j-c-end, j-c-start, j-c-between, j-c-around -->
      <div class="col-md-3">
        <div class="p-5 bg-primary text-light">col 1</div>
      </div>
* With contains show like rows in small screen and like columns in screen larger than ipads (md). in the class row we apply the flex box style.