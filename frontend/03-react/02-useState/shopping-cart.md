## Changing Class-based components app to hooks app

# Location in Mac
/Users/carlosinfante/Desktop/coding-projects/winc-academy/frontend-course/MODULE9 - DEBUGGING and DOMAIN MODELING/REVIEW/react-hooks/useState/shopping-cart

# Location in GitHub
https://github.com/carloscfgos1980/React-useState-shoppingCart

# Goals:
- Change class React class based component to a React hook (useState)
- Reusable components
- Input form
- Todo list. Add items to the grocery list
- Shopping Cart. This function check if the item exists, if exist increase the amount, else add a new item. This a boiler plate function coz it takes two functions and use mapp-include which is not necesary only we are looking for a word inside a vale a not the entire value, like this case.
- Use state
- Cool css so the list will have different colors


* Containersss.js contains the codes in React class based, the old way. The challange was to trun this into a React hook

1. Create the app with npx
2. Clean de app (delete unnecessary files).
3. Check the structure of the given Class-based components app:
   https://github.com/WincAcademy/solutions-exercises/tree/master/react-groceries-list

4. Container.js:
   4.1 - Change (class Container extends React.Component) for (const Container = () => {)

   4.2 Use useState extention from React by changing this:
   constructor(props) {
   super(props);
   this.state = {
   groceryItems: [
   { id: 1, title: "Eggs" },
   { id: 2, title: "Cheese" },
   { id: 3, title: "Garlic" },
   ],
   shoppingListItems: [
   { id: 4, title: "Onions", amount: 1 },
   { id: 5, title: "Leeks", amount: 2 },
   ],
   };
   }

   for this:
   const [grocery, setGrocery] = useState([
   { id: 1, title: "Eggs" },
   { id: 2, title: "Cheese" },
   { id: 3, title: "Garlic" },
   ])
   const [cart, setCart] = useState([
   { id: 1, title: "Onions", amount: 1 },
   { id: 2, title: "Leeks", amount: 2 },
   ])

   4.3 Get rid of all (this).

   - Check all functions for changes. Too many to describe

     4.4 Get rid of:
     render() {}

   * This is very important

   5. Pass the function for the event listener. This guy changed the name of the function everytime he passed to a child component which made it difficult to follow and understand what is going on. I kept the name to the last child component. Also passed the name of the function everytime so I didn't have to use (props).

   - Also check for all (this) which an element from class-bassed components and delete all of them.

   6. App.css
      Check the nth so I know how to give different background colors to the list. Ex:

ul.app-list li {
padding: 0.5em;
margin: 2px;
background-color: rgb(235, 165, 165);
}

ul.app-list li:nth-child(2n + 1) {
background-color: rgb(199, 118, 118);
}

## I hope this explanation mades sense in the future
* It made sense! I will describe how the app works!

# Steps:
1. Add item to grocery List (todo List)
1.1 Container.js. Create the function:
    // addItemToGrocery Function (lin 17-30) to add (todo-list). Deep copy of the previos array of objects (grocery) and add the id which is calculated by adding lenght of grocery, cart plus 1. This is to make sure that the new item will have a consecutive number id. This is not really necessary. It could be just getting a ramdom id, the only aspect that is relevant is htat id has to be unique.
    const addItemToGrocery = (title) => {
        let newGrocery = [
            ...grocery,
            {
                id:
                    grocery.length +
                    cart.length +
                    1,
                title: title,
            },
        ]
        setGrocery(newGrocery)
    };
1.2 Containers.js. Pass the data from the grocery list array and the function(addItemToGrocery) to the component(Grocery):
                   <GroceryList
                    grocery={grocery}
                    addItemToGrocery={addItemToGrocery}
                    addGroceryItemToCart={addGroceryItemToCart}
                />
1.3 InputField.js Create a react variable(useState)
    // It is necessary create a react variable in order to catch the value of the input form (line 5)   
    const [input, setInput] = useState("");

1.4 InputField.js. Create a function to attact to the onChange event:
    // onButtonPress function will be attact to the button as onClick event. Check if the value exist and call addItemToGrocery(input) and set the initial value of the react variable again to "" so it will erased what we type in the DOM automatically. In this case we dont need to pass a value to the funtion attatch to the onClick event coz the value come from the input form. 
    const onButtonPress = () => {
        if (input.length > 0) {
            console.log(`Submitting ${input}`);
            addItemToGrocery(input);
            setInput("");
        }
    }
1.5 Return the form that will catcth the value and add it to the grocery array of objects (items)
        <div className="input-field">
            <input
                type="text"
                value={input}
                onChange={(e) => setInput(e.target.value)}
            />
            <button onClick={onButtonPress} placeholder="Add a grocery item" >
                Add
            </button>
        </div>
    );


2. Add grocery to the cart
2.1 Containers.js. Create the funtion to add the new item to the cart:
 // addAmountToItem function (lin 32- 44) check if the item already exist and then add 1 to the amount. This function is called inside addGroceryItemToCart
    const addAmountToItem = (item) => {
        let existingtItems = cart.map((listItem) => {
            if (listItem.title === item.title) {
                {
                    listItem.amount = listItem.amount + 1
                };
            }
            console.log("List Items", listItem)
            return listItem;
        });

        setCart(existingtItems)
    };

    // addGroceryItemToCart function (lin 48-69) check if the item exists the call the function  addAmountToItem in order to add the amount. If the item does not exist then deep copy of cart and add the new item (lin 58-63). Set the updated array (setCart(newItemCart)).
    // This is a bit of a boiler plate. I could have make just one function. with a condiction to check if the item exist by mapping the array and just check for the title, include product title. also gives a different name of the parameter of the function and the iem thru the mapping, using itam for both would create a bug.
    const addGroceryItemToCart = (item) => {
        console.log(`addGroceryItemToCart: ${item.title}`);
        if (
            cart
                .map((item) => item.title)
                .includes(item.title)
        ) {
            addAmountToItem(item);
        } else {

            let newItemCar = [
                ...cart,
                {
                    id: cart.length + 1,
                    title: item.title,
                    amount: 1,
                },
            ]
            console.log("new Item Car", newItemCar)
            setCart(newItemCar)
        }
    };
   2.2 Containers.js. Pass the data from the grocery list array and the function(addGroceryItemToCart) to the component(Grocery):
                   <GroceryList
                    grocery={grocery}
                    addItemToGrocery={addItemToGrocery}
                    addGroceryItemToCart={addGroceryItemToCart}
                />

2.3 List.js. Create <ul> and inside this loop thru the array (items = grocery). Pass the item, and the function addGroceryItemToCart
            <ul className="app-list">
                {items.map((item) => (
                    <ListItem
                        key={item.id}
                        item={item}
                        addGroceryItemToCart={addGroceryItemToCart}
                    />
                ))}
            </ul>

2.4 ListItems.js. Display <li> that contains the key (necessary in order to identify the element in the DOM), classNAme (styling in css file), Onclick event that fire an annonymous callback function, and set the vale to the item.title
        // Apply addGroceryItemToCart(item) in this case we need to use an annonymous callback function so we pass the value of the selected item to the funtion (lin 7)
        <li
            key={item.id}
            className="list-item"
            onClick={() => addGroceryItemToCart(item)}
            value={item.title}

2.5 ListItems.js. Show the value in the DOM
            <div>{item.title}</div>

2.6 ListItems.js. Condictional rendering that check if item.amount exist and the render the div that show this data on the DOM. In this case item.amount does not exis so nothing will be show in the shoppinglist. Nevertheless List component will be used also for shoppingCart list which does contain item.amount
            {item.amount && (
                <div className="item-amount">Amount: {item.amount}</div>
            )}

3. Handle shopping cart list
3.1 Containers.js: Create a function(emptyCart) to delete all items from the shoppung cart
    // emptyCart function (lin 71-73) erase everything inside the cart array by setting to null. setCart([])
    const emptyCart = () => {
        setCart([]);
    };
3.2 Containers.js. Pass the data grom the shopping cart and the delete fuction to shoppingCart component.
                <ShoppingCart
                    cart={cart}
                    emptyCart={emptyCart}

                />

3.3 ShoppingCart.js. onClick event attact to delete button in order to clear the shopping cart list
            <button onClick={emptyCart} >Empty the shopping cart</button>

3.4 Passing the data to List.
            <List items={cart} />

* From this part is just repeat the steps from 2.3 to 2.6. by doing this: <List items={cart} /> then we can reuse List.js and ListItem component because we can give a different vale to item.

# THE END