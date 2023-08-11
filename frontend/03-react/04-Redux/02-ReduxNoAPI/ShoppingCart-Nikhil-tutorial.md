## Redux ShoppingCart-app with no API

Watch the tutorial from min 24 till 37
https://www.youtube.com/watch?v=zrs7u6bdbUw

# Location in Mac:
/Users/carlosinfante/Desktop/coding-projects/winc-academy/frontend-course/MODULE9 - DEBUGGING and DOMAIN MODELING/REVIEW/redux/tutorials/2. NoAPI/Redux-Shopping-Cart-App-Nikhil

# Location in GitHub:
https://github.com/carloscfgos1980/React-Redux-Toolkit-shoppingcart-Nikhil_tutorial

# Goals:
- Redux Toolkit. It an immer package that allows us to mutate the state. 
- ConfigureStore (reducer, export actions, export store)
- Store
- Form (very simple, only submit button)
- onSubmit event
- CSS. Form and buttons
- Add items to the store. Check if the product exist. If it does, just increase the amount and the total value. If it does not, then and the product to the shopping list. I like this method, it is very consistent!
- Show the amount of item in the shopping cart. Create a state for this and update it inside the add items to the list.
- Erase the item from the list is the amount is 1 or decrease the amount of item from the list if the amount is more than 1
- forEach in order to add the total amount



## Steps:

0. Clean the app. Same as other react app "cleanning". DO NOT DELETE App.css coz it will add extra margin.
   N: In this app, the style are not defined in App.css as usual, instead the style is applied in separately .css files that are attached to the components.

## 1. Create functionality to Log in

## 2. Log out functionability

1. Download the setup app from:
   https://github.com/Nikhilthadani/Redux-Shopping-Cart-App
   N: Check for starting app.

2. npm install

3. Create the auth-slice in the store folder. Check src/store/auth-slice.
   N: Other developers prefer to label this folder as redux.
   In this case inside redux there is a file named index.js. Other developers name this very same file store and redux to the folder that contains it.
   Nikhil uses "auth-slice" but most of the people would use camel notation so it would be like "authSlice".
   Nijhil also doesnt use the distress method on the export actions. Explanation in "src/store/auth-slice.js" and "src/store/index.js"

3.1 - Create reducer "login".
const authSlice = createSlice({
    name: 'auth',
    initialState: { isLoggIn: false },
    reducers: {
        login(state) {
            state.isLoggIn = true;
        },

3.2 - Create reducer "logout".
3.3 - Export actions. There are 2 ways of doing this. Explanation in auth-slice.js:
export const authActions = authSlice.actions;
/*
This from above could be also like this
export const {login, logout} = authSlice.actions;

N: By distrassing the function, we can call the function directly. Example in src/store/index.js
*/

3.4 Export this slice (configurestore)
export default authSlice;

4. src/store/index.js: Create the store from the configureStore.
const store = configureStore({
    reducer: {
        auth: authSlice.reducer,

5. Pass the state of <isLogging> to the app so it will show the Log in form when we are logged out and it wil will show the cart when we are logged in
5.1 useSelect hook to grab the state of <isLoggIn> from the store
  const isLoggedIn = useSelector(state => state.auth.isLoggIn);)
5.2 Condictional rendering to either show the Log in form or the shopping cart
      {!isLoggedIn && <Auth />}
      {isLoggedIn && <Layout />}


6. src/components/Auth.js In this example we don grab any value from the form. Only attact an event of submit so it will dispatch an action that change the state of <isLoggIn> and allow as to switch from the form layout to the shopping cart:
6.1 - Create the eventHandler to submit the action:
<form onSubmit={handleSubmit}>

6.2 - Import useDispatch

6.3 - Create the function "handleSubmit". Checkout notes in this file
  const handleSubmit = (e) => {
    e.preventDefault();
    dispatch(authActions.login());
    /* If we distress the actions export in the configureStore(auth-slice), then we could do it just like this
    dispatch(login());
    */
  }

## 2. Log out functionability. Explanation 1:06 hr -1:08

1. src/components/Header.js: "
1.1 - Create a button inside the list:
   <li>
   <button className="logout-btn">Logout</button>
   </li>
1.2 - Create the eventHandler attached to the button
<button onClick={logoutHandler} className="logout-btn">Logout</button>

1.3 - Create constanst "dispatch" and call "useDispatch"
const dispatch = useDispatch();

1.4 Create function "logoutHandler" ( lin 8 - 10)

2. Style the button:
   src/components/Layout.css (lin 13 - 20)


------------------------------------------------------------------------

## Redux ShoppingCart-app with no API

Watch the tutorial from min 37 till 1:08 hr
https://www.youtube.com/watch?v=zrs7u6bdbUw

# Goals:
- Add items to the store. Check if the product exist. If it does, just increase the amount and the total value. If it does not, then and the product to the shopping list. I like this method, it is very consistent!
- Show the amount of item in the shopping cart. Create a state for this and update it inside the add items to the list.
- Erase the item from the list is the amount is 1 or decrease the amount of item from the list if the amount is more than 1
- forEach in order to add the total amount


# 1. Add items to the store. Explanation: min 37 - 48

1. src/store/index.js: Create a file "cart-slice.js"

1.1 - Create the function "cartSlice".
1.2 Export the actions (reducers):
export const cartActions = cartSlice.actions;

1.3 - Export this configureStore:
export default cartSlice;

1.4 - Create all the initial states (line 6 - 10).
1.5 - Create reducers.

1.5.1 - Create the reducer to add items to the car:
addToCart(state, action)
1.5.2 - Create a const that will store the data (payload) that comes from the submit button.
const newItem = action.payload;

1.5.3 - Check if the item already exist:

                const existingItem = state.itemsList.find((item) => item.id === newItem.id);
            if (existingItem) {
                existingItem.quantity++;
                existingItem.totalPrice += newItem.price;
            }

1.5.4 - ELSE add the item:

                    state.itemsList.push({
                    name: newItem.name,
                    id: newItem.id,
                    quantity: 1,
                    totalPrice: newItem.price,
                    price: newItem.price
                });

N: Mutate the state. changed so it will show or not in the layout cart list once we make the changes (lin 13):
state.changed = true;

2. src/store/index.js: Add cart-slide to the store (lin 13):
   cart: cartSlice.reducer,

3. src/components/Product.js:
   3.1 - Add eventHandler to the button:
   <button onClick={addToCart}>Add to cart</button>

3.2 - Call useDispatch

3.3 - Create "addToCart". (lin 9 - 21). Explanation in "src/components/Product.js".
  const addToCart = () => {
    dispatch(
      cartActions.addToCart({
        /*
  If we distress the actions in cart-slice the we can just do:
  "addToCart" instead of "cartActions.addToCart"
  */
        name, // it really is "name:name," but in JXS is not needed so we only do "name,"
        id,
        price,
      })
    );
  };


# 2. Increase the amount of items. Explanation min 48 - 50

1. src/store/cart-slice.js:Change the state of the totalQuantity(line 30)

state.totalQuantity++;

N: We do it with the same reducer coz we just need to update "state.totalQuantity". We do it next to add new item to the cart so it is in the else statement.

2. src/components/Cart.js. Create a constant that containts the totalQuantity state (in the store) by using useSelector.
   const quantity = useSelector(state => state.cart.totalQuantity);

3. Display the amount of items on the DOM
<h3>Cart: {quantity} Items</h3>

This just display the amount of type of the items(in this case the laptops brands). It doenst display the total amount.
If we want to show the whole amount we need to use the reduce method on itemsList.totalQuantity

# 3. Show cart min. Explanation: 50-53

3.1 CartItems.js Create a const to grab the value in the store that contains the the array of objects (itemList) by using useSelector:
   const cartItems = useSelector(state => state.cart.itemsList);

3.2 CartItems.js. Map "cartItems" in order to send to "CartItem.js" the following value. We structure all the data inside <ul> and <li> so the data to be show will have this structure. Very smart!:
      <ul>
        {cartItems.map((item) => (
          <li key={item.id}>
            {" "}
            <CartItem
              quantity={item.quantity}
              id={item.id}
              price={item.price}
              total={item.totalPrice}
              name={item.name}
            />{" "}
          </li>
        ))}
      </ul>

3.3 Get the data from the mapping in <CartItems.js> into the function (CartItem)
const CartItem = ({ name, quantity, total, price, id }) => {

3.4 Return the values that will be shown in the DOM. This are show as a List cos we set this up in <CartItems.js>
  return (
    <div className="cartItem">
      <h2> {name}</h2>
      <p>${price} /-</p>
      <p>x{quantity}</p>
      <article>Total ${total}</article>
      <button className="cart-actions" onClick={removeHandler}>
        -
      </button>
      <button className="cart-actions" onClick={addHandler}>
        +
      </button>
    </div>
  );



# 4. Show Cart functionability. Explanation: 53-55

1.  src/store/cart-slice.js: Create the reducer "setShowCart". In order to be able to click on the button amount and show the list once we have added at list one element and the list will disappear if we delete all items. (lin 45 -47).
        setShowCart(state) {
            state.showCart = !state.showCart; // allows to swith from true to false everytime we call this function. USeful to show the info in the DOM
        }

2.  src/components/Cart.js: Create the eventHanler attached to the button in order to show the list of added items.
    2.1 Grab the state of showCart:
      const quantity = useSelector(state => state.cart.totalQuantity);

    2.2 - Create the const "dispatch" and call "useDispatch".
    2.3 - onClick to the button:
    <h3 onClick={showCart}>Cart: {quantity} Items</h3>
    2.4 - Create the "showCart" function. (lin 10 -12).
      const showCart = () => {
    dispatch(cartActions.setShowCart());
  }

3.  src/components/Layout.js:
    3.1 - Get the "showCart" state (store):
    const showCart = useSelector(state => state.cart.showCart);
    3.2 - Conditional rendering with the && operator

            {showCart && <CartItems />}

# 5. Functionability to reduce and increse the amount in the layout Cart list. Explanation min 55 - 1:03 hr

5.1 src/store/cart-slice.js: Create reducer "removeFromCart". Just like add items. We check if the I'tem exist and then remove it completely only if the amoung is 1, if there is more than one, then just decrease the amount and total value.
        removeFromCart(state, action) {
            state.changed = true;
            const id = action.payload;

            const existingItem = state.itemsList.find((item) => item.id === id);
            if (existingItem.quantity === 1) {
                state.itemsList = state.itemsList.filter(item => item.id !== id)
            } else {
                existingItem.quantity--;
                existingItem.totalPrice -= existingItem.price
            }
        },

5.2 src/components/CartItem.js:
5.2.1 - Create const "dispatch" and call "useDispatch"
const dispatch = useDispatch();

5.2.2 - Create eventHandlers to remove and add items:

      <button className="cart-actions" onClick={removeHandler}>
      <button className="cart-actions" onClick={addHandler}>

5.2.3 - Create "removeHandler" (lin 7 - 9)
  const removeHandler = () => {
    dispatch(cartActions.removeFromCart(id));
  };

5.2.4 -Create "addHandler" (lin 10 -18)
  const addHandler = () => {
    dispatch(
      cartActions.addToCart({
        id,
        name,
        price,
      })
    );
  };
N: Same method we use to add items to the cart. Checkout "src/components.Product.js".

# 6. Increase the amount of money (total value from the items in the cart) Explanation 1:04.

src/components/Layout.js

1. Create a variable equal to 0
   let total = 0;

2. Get "itemList" from the store (useSelector)
   const itemList = useSelector(state => state.cart.itemsList);

3. Increasing the amount using forEach high order array method:
   itemList.forEach(item => {
   total += item.totalPrice;
   })
