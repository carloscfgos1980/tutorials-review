## Add Items to the cart.
* Checking that if the item is the list and updating the state. If it doesn't exist then add an item

1. Nikhil Shopping cart. This way is much better than the shopping cart method (2)

# Location in Mac:
/Users/carlosinfante/Desktop/coding-projects/winc-academy/frontend-course/MODULE9 - DEBUGGING and DOMAIN MODELING/REVIEW/redux/tutorials/2. NoAPI/Redux-Shopping-Cart-App-Nikhil

# Location in GitHub:
https://github.com/carloscfgos1980/React-Redux-Toolkit-shoppingcart-Nikhil_tutorial

        addToCart(state, action) {
            const newItem = action.payload;
            // To check if the item is already available
            const existingItem = state.itemsList.find((item) => item.id === newItem.id);
            if (existingItem) {
                existingItem.quantity++;
                existingItem.totalPrice += newItem.price;
            } else {
                state.itemsList.push({
                    name: newItem.name,
                    id: newItem.id,
                    quantity: 1,
                    totalPrice: newItem.price,
                    price: newItem.price
                });
                state.totalQuantity++; // increase the total quantity
            }
        },

2. Shoppingcart Winc Academy updated:
       addGroceryItemToCart: (state, action) => {
            if (
                state
                    .map((item) => item.title)
                    .includes(action.payload.title)
            ) {
                let existingtItems = state.map((listItem) => {
                    if (listItem.title === action.payload.title) {
                        listItem.amount = listItem.amount + 1
                    })
                    return listItem;
                });
                state = existingtItems
            }
            let newItemCart =
            {
                id: Date.now(),//This create unique ids based in the current time
                title: action.payload.title,
                amount: 1

            };
            state.push(newItemCart);
        }


## Erase items from the cart or decrease the amount. Nikhil shopping cart tutorial

5.1 src/store/cart-slice.js: Create reducer "removeFromCart". Just like add items. We check if the I'tem exist and then remove it completely only if the amoung is 1, if there is more than one, then just decrease the amount and total value.
        removeFromCart(state, action) {
            const id = action.payload;
            const existingItem = state.itemsList.find((item) => item.id === id);
            if (existingItem.quantity === 1) {
                state.itemsList = state.itemsList.filter(item => item.id !== id)
                state.totalQuantity--; //decrease the amount of total quantity and update the amount in the shopping cart
            } else {
                existingItem.quantity--;
                existingItem.totalPrice -= existingItem.price
            }
        },
