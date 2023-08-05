## BOOTSTRAP TUTORIAL
* This is a HTML and plan Vanilla JavaScript project
# Location in Mac:
/Users/carlosinfante/Desktop/coding-projects/winc-academy/frontend-course/MODULE9 - DEBUGGING and DOMAIN MODELING/REVIEW/Bootstrap/bootstrap-The_Net_Ninja
* There are a bunch of lessons. This is the root file

# Location in GitHub:
https://github.com/carloscfgos1980/Bootstrap-JavaScript-NetNinja-tutorial

# Lesson 1. Intro and Set up
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

# Lesson 2. Bootstrap 5 new features
https://www.youtube.com/watch?v=YQRmczOYIG0&list=PL4cUxeGkcC9joIM91nLzd_qaH_AimmdAR&index=2

# Lesson 3. Color and Typography
https://www.youtube.com/watch?v=iUCyU_U0J2E&list=PL4cUxeGkcC9joIM91nLzd_qaH_AimmdAR&index=3
# Goals:

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
