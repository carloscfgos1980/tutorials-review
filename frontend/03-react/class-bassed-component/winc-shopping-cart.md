## Shopping cart

Location on Mac:
/Users/carlosinfante/Desktop/coding-projects/winc-academy/frontend-course/MODULE9 - DEBUGGING and DOMAIN MODELING/REVIEW/react-class-based-components/Winc-shoppingCart

Location in GitHub:
https://github.com/carloscfgos1980/React-ClassBased-ShoppingCart

# Goals:
- Class Based Component todo list
- Class Based Component use state
- Class Based Component add to the cart new Item if it does not exit or just increment the amount if existe(lopping with map and include example) 
- reuseable components.
- style same component differently, dependong where it is displayed. App.css (lin 31-47)


* This is a app given by Winc Academy. It was confusing at first coz they passed the function to the componenets and changed 3 times the name of the function

* This is  combination of todo list with shopping cart
# Steps
1. Passing the state and function to add items to the grocery list (todo list)
* Confusing cos they changed the name of the function (onItemAdd={this.addItemToGroceryList})
1.1 Container.js 
     addItemToGroceryList = (title) => {
        this.setState({
            groceryItems: [
                ...this.state.groceryItems,
                {
                    id:
                        this.state.groceryItems.length +
                        this.state.shoppingListItems.length +
                        1,
                    title: title,
                    amount: 1,
                },
            ],
        });
    };   

                    id:
                        this.state.groceryItems.length +
                        this.state.shoppingListItems.length +
                        1,
* This gives id to the new item that is the sum of the amount of itmes in the grocery list and in the shopping cart plus 1.
* example of deep copying and then add a new item (object)

<GroceryList
                        items={this.state.groceryItems}
                        onItemClick={this.addGroceryItemToCart}
                        onItemAdd={this.addItemToGroceryList}

1.2 GroceryList.js
            <h2>Shopping list</h2>
            <InputField onSubmit={onItemAdd} />
            <List items={items} onItemClick={onItemClick} />

1.3 InputField.js:
    function onButtonPress() {
        if (inputValue.length > 0) {
            console.log(`Submitting ${inputValue}`);
            onSubmit(inputValue);
            setInputValue("");
        }
    }

            <button onClick={onButtonPress} placeholder="Add a grocery item">
                Add
            </button>


2. Add Item to the grocery cart:
* This is a confusing method coz they changed the name several times (onItemClick={this.addGroceryItemToCart})
and they used 2 functions. <addAmountToItem> is inside <addGroceryItemToCart>
2.1 Container.js
    addAmountToItem = (item, amount) => {
        this.setState({
            shoppingListItems: this.state.shoppingListItems.map((listItem) => {
                if (listItem.title === item.title) {
                    return {
                        id: listItem.id,
                        title: listItem.title,
                        amount: listItem.amount + amount,
                    };
                }
                return listItem;
            }),
        });
    };

    addGroceryItemToCart = (item) => {
        console.log(`addGroceryItemToCart: ${item.title}`);
        if (
            this.state.shoppingListItems
                .map((item) => item.title)
                .includes(item.title)
        ) {
            this.addAmountToItem(item, 1);
        } else {
            this.setState({
                shoppingListItems: [
                    ...this.state.shoppingListItems,
                    {
                        id: item.id,
                        title: item.title,
                        amount: 1,
                    },
                ],
            });
        }
    };
                    <GroceryList
                        items={this.state.groceryItems}
                        onItemClick={this.addGroceryItemToCart}
                        onItemAdd={this.addItemToGroceryList}
                    />

2.2 GroceryList.js: Passing the state and the function to List.js component
            <List items={items} onItemClick={onItemClick} />

2.3 List.js: looping thru the array of objects (items) and passing (to ItemLists.js) the function again to add to the shopping cart. Tnis time the name is not changed

                    {this.props.items.map((item) => (
                        <ListItem
                            key={item.id}
                            item={item}
                            clickItem={() => this.props.onItemClick(item)}
                            showQuantities={this.props.showQuantities}
                        />
                    ))}
2.3 LsitItems.js


3. Shopping cart. Here nothing much happens. Only display a list with the items in the shopping cart and empty the shopping cart.

3.1 Container.js:
* this function is passed to the shopping cart but only log to the console the clicked values!,. The other function is to erase the items from the cart.
    handleClickGroceryItem(item) {
        console.log(`Clicked ${item.id}: ${item.title}`);
    }


                    <ShoppingCart
                        items={this.state.shoppingListItems}
                        onItemClick={this.handleClickGroceryItem}
                        onEmptyClick={this.emptyCart}
                    />

3.2 ShoppingCart.js:
            <button onClick={onEmptyClick}>Empty the shopping cart</button>
            <List items={items} onItemClick={onItemClick} showQuantities={true} />
* in this case <showQuantities> gets a value of true. This is passed to the reusable component (List, ListItems) so it would display the amount of items in the shopping cart and dismiss this element when in the grocery list without breaking the app. 

3.3 List.js:
            <div>
                <ul className="app-list">
                    {this.props.items.map((item) => (
                        <ListItem
                            key={item.id}
                            item={item}
                            clickItem={() => this.props.onItemClick(item)}
                            showQuantities={this.props.showQuantities}
                        />
                    ))}
                </ul>
            </div>

3.4 ListItems.js:
        <li
            key={item.id}
            className="list-item"
            onClick={clickItem}
            value={item.title}
        >
            <div>{item.title}</div>
            {showQuantities && (
                <div className="item-amount">Amount: {item.amount}</div>
            )}
        </li>
*Using conditional rendering. It checks if <showQuantities> is true and then render what is on the rigt, in this case, the amount.:
            {showQuantities && (
                <div className="item-amount">Amount: {item.amount}

# Cool CSS
* This gives a color to a unpair list and a different color to the pair list. The other thing is that thei are reusing components so the way to grab the apart is by using the parent element in the shopping cart (.shopping-cart ul.app-list li)

  ul.app-list li {
    padding: 0.5em;
    margin: 2px;
    background-color: rgb(235, 165, 165);
  }
  
  ul.app-list li:nth-child(2n + 1) {
    background-color: rgb(199, 118, 118);
  }
  
  .shopping-cart ul.app-list li {
    background-color: rgb(165, 181, 235);
  }
  
  .shopping-cart ul.app-list li:nth-child(2n + 1) {
    background-color: rgb(127, 142, 190);
  }