## BOOTSTRAP TUTORIAL
* This is a HTML and plan Vanilla JavaScript project

# Location in Mac:
/Users/carlosinfante/Desktop/coding-projects/winc-academy/frontend-course/MODULE9 - DEBUGGING and DOMAIN MODELING/REVIEW/Bootstrap/bootstrap-The_Net_Ninja
* There are a bunch of lessons. This is the root file

# Location in GitHub:
https://github.com/carloscfgos1980/Bootstrap-JavaScript-NetNinja-tutorial_I
* Lesson 1 to 7

https://github.com/carloscfgos1980/Bootstrap-JavaScript-NetNinja-tutorial_II
* Lesson 8 to 20

# INDEX
<Lesson 1. Intro and Set up>
# Goals:
- Conceptual definition of bootstrap

<Lesson 3. Color and Typography>
# Goals:
- Text style: headings, display, lead & alignment, text decorarion & font weight, colors, background colors

<Lesoon 4. Buttons & Button Groups>
# Goals:
- Buttons: basic, anchor tag, size, outline(hover)

<Lesson 5. Utility classes>
# Goals:
- Classes: margin, padding, borders, box shadow, font weight

<Lesson 6 - Containers>
# Goals:
- Containers: Customize the width of the content in our page and adjust it to different point view (type of devise)

<Lesson 07 - Grid Layout (part 1)>
# Goals:
- Grid layout. We use this to organize the content in the DOM.
* By default the screen is divided in 12 columns!

<Lesson 08 - Grid Layout (part 2). Create the app>
# Goals:
- Section # 1
- Containers
- Grid Layouts: Felx box
- Text style
- use imgage: small screen does not display and large does.

<Lesson 09. Navbars>
# Goals:
- NavBar
- Container xxl

<Lesson 10. Cards>
# Goals:
- Cards
-Containers
- Show the text only in larger screen: d-none d-lg-block
- ourline button. It colors by bover over it. 
- gap. g-0. Cero gap so there is no space between the cards.

<Lesson 11 - Accordions>
# Goals:
- Accordion
- Image
-  Container
- Grid: Flex Box

<Lesson 12. List Groups>
# Goals:
- List
- Container
- Grid layout

<Lesson 13. Bootstrap Icons>
# Goals:
- Icons

<Lesson 14. Working with Forms>
# Goals:
- Forms
- Icons

<Lesson 15. Tooltips>
* tooltips is the message that appear when we hover the mouse over certain element. In This example is when it hovered over the book image and over the input field of email.
* This is HTML page and for tooltip we need javascript.

<Lesson 16. Modals>
# Goals:
- Modals. Message tha pops out with extra info by clicking a button
- Form. In the modal message.
- Grid layer

* This is the message that pops up. I dont plant to use for now so just know that it is possible. Example index.html (lin 411 - 451)

<Lesson 17. Offcanvas>
# Goals:
- Offcanvas. This is a feature to create sideBar. I wont be using it but is good to know that exist...

<Lesson 19. Customizing Bootstrap>
* I tried this once and it is a pain in the ass. It is easier to creat a claas the and style this specific item in CSS file.

<Lesson 20. Tabs>
This is to create a sort of NabBar but instead of take us to a new page, it just show new content. I wont be using any time soon but yet it is important to know that exist!

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


## Lesoon 4. Buttons & Button Groups
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

# Goals:
- Grid layout. We use this to organize the content in the DOM.
* By default the screen is divided in 12 columns!

7.1 Basic grid.  Divide the columns equally (lin 5 -28). EX
  <div class="container-lg my-5">
    <h2>basic grid</h2>
    <div class="row">
      <div class="col">


7.2. Set the columns with different size. (lin 30 -43)
  <div class="container-lg my-5">
      <div class="col">
  <div class="container-lg my-5">
  <div class="row">
   <div class="col-6">
   <div class="col-3">
    <div class="col-3">

7.3 Responsive column widths (lin 45 -59). Small screen they look like columns and larger than small screen the look like rows:

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

7.4 justifying column. 
  <div class="container-lg my-5">
    <h2>justifying columns</h2>
    <div class="row justify-content-center">
      <!-- j-c-end, j-c-start, j-c-between, j-c-around -->
      <div class="col-md-3">
        <div class="p-5 bg-primary text-light">col 1</div>
      </div>
* With contains show like rows in small screen and like columns in screen larger than ipads (md). in the class row we apply the flex box style.


## Lesson 08 - Grid Layout (part 2). Creating the app
https://www.youtube.com/watch?v=yCCIztB-S_k&list=PL4cUxeGkcC9joIM91nLzd_qaH_AimmdAR&index=8

# Goals:
- Section # 1
- Containers
- Grid Layouts: Felx box
- Text style
- use imgage: small screen does not display and large does.

8.1 This section has a text on the right and image on the left.

8.2 Section will have an "id" so we could scroll to those sections with the NavBar

8.3 In the Head component is some padding style applied. Normaly we do that in a css file and imported to the index.html:
     <style>
       section {
         padding: 60px 0;        // 60px to the to and to the botton
       }
     </style>
   </head>

8.4 Inside the section, create a grid
<div class="container-lg">      // Every grid goes into a container. This means it will be 100% until it reach the "large break point" (lg). When it reach the breaking point it goes to the center kinda structure.

8.5 Inside <div class="container-lg"> :
<div class="row justify-content-center align-items-center">         
// "justify-content-center" - Everything inside this <div> will be align to the center
// align-items-center" - in the Y Axis (horizontal, from top to botton) everything will be in the center.

8.6 Inside <div class="row justify-content-center"> : Create two colums of content( on the right some text and on the left, an image):

8.7 - Create the Div para la comlumna de la izquierda

<div class="col-md-5 text-center text-md-start">
// "m-5" means that it will be 100 % (12 grid-columns in width) for extra small size screens and then when it reaches the medium size screen getting bigger, at that point we are getting 5 columns of width for this element
// "text-center text-md-start" It means that the content will be centered for small size screens and when it reaches the medium breaking point, it move to the right (text-md-start).

8.8 Create content of the column on the left:
Inside <div class="col-md-5 text-center text-md-start">

   <h1> // First time I see a div inside <h1>
   <div class="display-2">Black-Belt</div> //class="display-2" size of the text. Lower number, bigger letter size.
   <div class="display-5 text-muted">Your Coding Skills</div>
   </h1>
   <p class="lead my-4 text-muted">Lorem ipsum dolor sit amet consectetur adipisicing elit. Laboriosam,
   dignissimos?</p> //to Generate random text, type: Lorem and press "tab".
   // "my-4" - to give margin top and botton.
   // "text-muted" - to give a gray color to the text
   <a href="#pricing" class="btn btn-secondary btn-lg">Buy Now</a> // anchor tag with the shape of a button
   // "btn-secondary" - give the button the secundary default color
   // "btn-lg" - Make the button larger.

8.9 - Create content of the column on the right. This will contain the image:
Inside <div class="row justify-content-center">

<div class="col-md-5 text-center d-none d-md-block"> //This works to centralize the image as well. This doesnt work in css so it makes our work a lot easier.
// "d-none d-md-block" - It means that as default (small size screens) it will not display the content inside this <div>, in this case the image, and it will show it when it gets to the break point of medium size screens (d-md-block)

8.10 Image
<img src="/assets/ebook-cover.png" class="img-fluid" alt="ebook"> // It makes is 100% width of the parent element(in this case is 5: <div class="col-md-5)

## Lesson 09. Navbars
https://www.youtube.com/watch?v=7AT1X9Z41sA&list=PL4cUxeGkcC9joIM91nLzd_qaH_AimmdAR&index=9

# Goals:
- NavBar
- Container xxl


* In order to apply the NavBar, we go to the Bootstrap website:
https://getbootstrap.com/docs/5.2/getting-started/introduction/
And find the NavBar tht we want. Then just copy

This part of the NavBar is to have a variation of the same link. When the screen is small it will display a text and when it is bigger than medium size, it will display a button. Explanation in the video

          <li class="nav-item d-md-none">
            <a class="nav-link" href="#pricing">Pricing</a>
          </li>
          <li class="nav-item ms-2 d-none d-md-inline">
            <a class="btn btn-secondary" href="#pricing">buy now</a>
          </li>

## Lesson 10. Cards
https://www.youtube.com/watch?v=NRoET8-8cbw&list=PL4cUxeGkcC9joIM91nLzd_qaH_AimmdAR&index=10

# Goals:
- Cards
-Containers
- Show the text only in larger screen: d-none d-lg-block
- ourline button. It colors by bover over it. 
- gap. g-0. Cero gap so there is no space between the cards.

1. Search in the bootstrap website, what kind of card we want
   https://getbootstrap.com/docs/5.2/getting-started/introduction/

N: This cards is is used to display a product, little description and a link to something else, like buying the product. So far I dont need to use use it in my DashBoard-app project

* This example is displayed in index.html (lin 80 -136)
* To create a grid we need always to put everything inside a <div class='row'>, like this:
<div class="row my-5 g-0 align-items-center justify-content-center">
"my-5" - to git a margin top and botton of 5.
"g-0"- To eliminate the default gap between the cards
"align-items-center" - To place all the elements in the center (horizontally - X Axis)
"justify-content-center" - To place all the elements in the center (vertically -Y Axis )

---

- In this case we have 3 cards. The one in the middle is sligthly bigger that the one the right and left. We do it like this:

        <div class="col-8 col-lg-4 col-xl-3">   //"col-8" - It is size (8 is the amoung of grid-collumns).
        <div class="col-9 col-lg-4">    //"col-9" This is why is a bit bigger
        <div class="col-8 col-lg-4 col-xl-3">

        About the responsiness:
        "class="col-8 col-lg-4 col-xl-3". Start in small screens with a size of 8 grid-columns, then in large size (lg-4), takes 4 grid-columns and in extra large screens (col-xl-3) it reduce size of the grid columns to 3. In reallity, we are going to observe the cards in the more or less same size since the variation of size is a percent of the screen and not physical unit meassure like centimeters.
        "class="col-9 col-lg-4" in this case only onces it gets to large screens (col-lg-4)

- There are many variations of cards. I just need time to play around in select the one I need and like

## Lesson 11 - Accordions
https://www.youtube.com/watch?v=cVThXv6hYW0&list=PL4cUxeGkcC9joIM91nLzd_qaH_AimmdAR&index=11

# Goals:
- Accordion
- Image
-  Container
- Grid: Flex Box

This is to create acording text. The only thing we have to check are that the "id"s match. It is a bunch of codes but I just copy everything from
https://getbootstrap.com/docs/5.2/getting-started/introduction/

Check the example in index.html (lin 139 - 253)

## Lesson 12. List Groups
https://www.youtube.com/watch?v=gwgeMole3gs&list=PL4cUxeGkcC9joIM91nLzd_qaH_AimmdAR&index=12

# Goals:
- List
- Container
- Grid layout

* This feature is gonna be very important in order to style "todo list"
Example in index.html (lin 256 - 297)

If we only need that the content varias from 100% to a certain sise when a larger screen, we do as bellow (lin 263):

<div class="row justify-content-center">
<div class="col-lg-8"></div>
</div>

## Lesoo 13. Bootstrap Icons
https://www.youtube.com/watch?v=rhvMRsE_6sY&list=PL4cUxeGkcC9joIM91nLzd_qaH_AimmdAR&index=13

# Goals:
- Icons

We can choose the Icon in the followed website:
https://icons.getbootstrap.com/

# Steps:
13.1 Copy the Link from bootstrap icon and copy in the <head>. This is for HTML, in REACT is completely different.
  <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.0.1/dist/css/bootstrap.min.css" rel="stylesheet"
    integrity="sha384-+0n0xVW2eSR5OomGNYDnhzAbDsOXxcvSN1TPprVMTNDbiYZCxYbOOl7+AMvyTG2x" crossorigin="anonymous">

31.2 Copy the icon and past it in our project:
lin 27:
<i class="bi bi-book-half"></i>

lin 261:
<h2><i class="bi bi-stars"></i>Book Reviews</h2>

Create 5 starts (books review) (lin 269 -275)

              <div class="pb-2">
                <i class="bi bi-star-fill"></i>
                <i class="bi bi-star-fill"></i>
                <i class="bi bi-star-fill"></i>
                <i class="bi bi-star-fill"></i>
                <i class="bi bi-star-fill"></i>
              </div>

Create 4 starts and a half (books review) (lin 297 - 303)

              <div class="pb-2">
                <i class="bi bi-star-fill"></i>
                <i class="bi bi-star-fill"></i>
                <i class="bi bi-star-fill"></i>
                <i class="bi bi-star-fill"></i>
                <i class="bi bi-star-half"></i>
              </div>

## Lesoon 14. Working with Forms
https://www.youtube.com/watch?v=dKVX22GR7zQ&list=PL4cUxeGkcC9joIM91nLzd_qaH_AimmdAR&index=14

# Goals:
- Forms
- Icons

- Styling forms is very usefull. Example in index.html (lin 343 - 393)

14.1 We have to create the section and give the id:
<section id="contact">

14.2 Place all the content in a large container so it will have 100% width till it heats large screen size:
<div class="container-lg">

14.3 We use a grid even when we are dealing with a single column coz that allows us to create a responsive form (it will adjust automatically the size of the content, in this case the form):
   <div class="row justify-content-center my-5">

14.4 Stablish the size of the contenr for a large screen, by defaul small screen is 100%:
   <div class="col-lg-6">

14.5 Create a group text. This is a very cool styling
   <div class="input-group mb-4">
   <span class="input-group-text">
   <i class="bi bi-envelope-fill text-secondary"></i>
   </span>
   <input type="text" id="email" class="form-control" placeholder="e.g. mario@example.com" />
   </div>

14.6 Cool styling by putting the label inside the text area
   <div class="mb-4 mt-5 form-floating">
   <textarea class="form-control" id="query" style="height: 140px" placeholder="query"></textarea>
   <label for="query">Your query...</label>
   </div>

## Lesson 15. Tooltips
https://www.youtube.com/watch?v=WTrW-1JsDYE&list=PL4cUxeGkcC9joIM91nLzd_qaH_AimmdAR&index=15

* tooltips is the message that appear when we hover the mouse over certain element. In This example is when it hovered over the book image and over the input field of email.
* This is HTML page and for tooltip we need javascript.

15.1  First we need to reate a function (JavaScript) at the end of the body (lin 416 - 422):
<script>
  const tooltips = document.querySelectorAll('.tt')
  tooltips.forEach(t => {
    new bootstrap.Tooltip(t)
  })
</script>

15.2  Tooltip over the book (lin 76 -78):

              <span class="tt" data-bs-placement="bottom" title="Net Ninja Pro book cover">
                <img src="/assets/ebook-cover.png" class="img-fluid" alt="ebook">
              </span>

    N: class="tt" is just a madeup name that we will use to loop over it with the function.

15.3  Tooltip for the email (367-369):

                        <span class="input-group-text">
                <span class="tt" data-bs-placement="bottom" title="Enter an email address we can reply to.">
                  <i class="bi bi-question-circle text-muted"></i>
                </span>

\*There are more examplle of tooltip in this app


## Lesson 16. Modals
https://www.youtube.com/watch?v=tt5uUMQgzl0&list=PL4cUxeGkcC9joIM91nLzd_qaH_AimmdAR&index=16

# Goals:
- Modals. Message tha pops out with extra info by clicking a button
- Form. In the modal message.
- Grid layer

* This is the message that pops up. I dont plant to use for now so just know that it is possible. Example index.html (lin 411 - 451)

## Lesson 17. Offcanvas
https://www.youtube.com/watch?v=aUVTxD5MasM&list=PL4cUxeGkcC9joIM91nLzd_qaH_AimmdAR&index=17

# Goals:
- Offcanvas. This is a feature to create sideBar. I wont be using it but is good to know that exist...

# Steps:
17.2 Inside section id="intro. Create the href to create the sideBar (offcanvas)
   <a href="#sidebar" class="d-block mt-3" data-bs-toggle="offcanvas" role="button" aria-controls="sidebar">
   Explore my other books
   </a>
   </div>

17.2 Create the elements for the sideBar (lin 457 - 468)

## Lesson 18. Dropdowns
https://www.youtube.com/watch?v=lu4HFx3bzy8&list=PL4cUxeGkcC9joIM91nLzd_qaH_AimmdAR&index=18

# Goals:
- create a Drown down button that shows other chocices. Normaly links.

* This is a button that show us elements inside the sideBar (offcanvas). I wont be using this but it is good to know that it exists
  Example in index.html (lin 468 - 477)


## Lesson 19. Customizing Bootstrap
https://www.youtube.com/watch?v=nCX3QVl_PiI&list=PL4cUxeGkcC9joIM91nLzd_qaH_AimmdAR&index=19

* i tried this once and it is a pain in the ass. It is easier to creat a claas the and style this specific item in CSS file.

## Lesson 20. Tabs
https://www.youtube.com/watch?v=IMM93WydBSw&list=PL4cUxeGkcC9joIM91nLzd_qaH_AimmdAR&index=20

This is to create a sort of NabBar but instead of take us to a new page, it just show new content. I wont be using any time soon but yet it is important to know that exist!

## THE END