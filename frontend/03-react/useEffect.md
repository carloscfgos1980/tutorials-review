## useEffect

1. useEffect as a custom hook for fetching data. The Net Ninja blog app
2. Post data. The Net Ninja blog app
* In the tutorial this works ok but when I tried in Song Gaver app it didn't updated the DOM so as return I used a javascrip code to refresh the page. This is not the way it should be. I believe is better to add a dependency to useFetch to it will fire a action everytime the data change
3. useEffect to PUT data from the app. Nikhil shopping cart app
4. useEffect to PUT data from the store. Nikhil shopping cart app
5. useEffect to FETCH data from the store. Nikhil shopping cart app


# 1. useEffect as a custom hook for fetching data. The Net Ninja blog app 
----------------------------------------------------------
The Net Ninja blog app in Mac:
/Users/carlosinfante/Desktop/coding-projects/winc-academy/frontend-course/MODULE9 - DEBUGGING and DOMAIN MODELING/REVIEW/react-hooks/useState nd useEffect/The_Net_Ninja-blog-app

The Net Ninja blog app in GitHub:
https://github.com/carloscfgos1980/React-useState-useEffect-blog

---------------------------------------------------------
useFetch.js:
import { useState, useEffect } from 'react';

const useFetch = (url) => {
  const [data, setData] = useState(null);
  const [isPending, setIsPending] = useState(true);
  const [error, setError] = useState(null);

  useEffect(() => {
    const abortCont = new AbortController();

    setTimeout(() => {
      fetch(url, { signal: abortCont.signal })
      .then(res => {
        if (!res.ok) { // error coming back from server
          throw Error('could not fetch the data for that resource');
        } 
        return res.json();
      })
      .then(data => {
        setIsPending(false);
        setData(data);
        setError(null);
      })
      .catch(err => {
        if (err.name === 'AbortError') {
          console.log('fetch aborted')
        } else {
          // auto catches network / connection error
          setIsPending(false);
          setError(err.message);
        }
      })
    }, 1000);

    // abort the fetch
    return () => abortCont.abort();
  }, [url])

  return { data, isPending, error };
}
 
export default useFetch;

# 2. Post data. The Net Ninja blog app
Home.js:
  const { error, isPending, data: blogs } = useFetch('http://localhost:8000/blogs')


  Create.js

      setIsPending(true);

    fetch('http://localhost:8000/blogs/', {
      method: 'POST',
      headers: { "Content-Type": "application/json" },
      body: JSON.stringify(blog)
    }).then(() => {
      setIsPending(false);
      // history.go(-1);
      history.push('/');
    })


-----------------------------------------------------------------------
# 3. useEffect to PUT data from the app. Nikhil shopping cart app

Nikhil shopping cart app in Mac:
/Users/carlosinfante/Desktop/coding-projects/winc-academy/frontend-course/MODULE9 - DEBUGGING and DOMAIN MODELING/REVIEW/redux/tutorials/2. NoAPI/Redux-Shopping-Cart-App-Nikhil

Nikhil shopping cart app in Github:
https://github.com/carloscfgos1980/React-Redux-toolkit-shoppingCart-Api_I



* Nikhil use Notifications which make the PUT action fuction a lot more complex. Explanation tutorial video from 1:13 to 1:28 hr:
- I need to create an slice (uiSlice) in the store the this purpose and pass it to the store.
- Create a Notification component with a dispatch so it will change the state inside tue uiSlice
- Call back the notifications 3 times inside the useEffect 
- Use function to stop render the notification when the page render for first time

      useEffect(() => {
    if (isFirstRender) {
      isFirstRender = false;
      return;
    }
    const sendRequest = async () => {
      //Send state as sending request
      dispatch(uiActions.showNotifications({
        open: true,
        message: 'Sending request',
        type: 'warning'
      }))
      const res = await fetch('https://api-shoppingcart-default-rtdb.firebaseio.com/cartItems.json', {
        method: "PUT",
        body: JSON.stringify(cart)
      }
      );
      const data = await res.json();
      // send state as a Request is successful
      dispatch(uiActions.showNotifications({
        open: true,
        message: 'Sent DATA to DataBase Successfully',
        type: 'success'
      }))
    }
    sendRequest().catch(err => {
      //Send state as error
      dispatch(uiActions.showNotifications({
        open: true,
        message: 'Sending request failed',
        type: 'error'
      }))
    });
  }, [cart])// By puting the cart dependency in the useEffect. it will update everytime we change the state (cart)

# 4. useEffect to PUT data from the store. Nikhil shopping cart app. 1:28 - 1:41 hr
https://www.youtube.com/watch?v=zrs7u6bdbUw
Location in Mac:
/Users/carlosinfante/Desktop/coding-projects/winc-academy/frontend-course/MODULE9 - DEBUGGING and DOMAIN MODELING/REVIEW/redux/tutorials/3. API

Location in GitHub:
https://github.com/carloscfgos1980/React-Redux-toolkit-shoppingCart-Api_II

1.3 src/store/cart-actions.js. Just copy the function we had inside App.js:
export const sendCartData = (cart) => {
    return async (dispatch) => {
        dispatch(uiActions.showNotifications({
            open: true,
            message: 'Sending request',
            type: 'warning'
        })
        );
        const sendRequest = async () => {
            //Send state as sending request
            const res = await fetch('https://api-shoppingcart-default-rtdb.firebaseio.com/cartItems.json', {
                method: "PUT",
                body: JSON.stringify(cart)
            }
            );
            const data = await res.json();
            // send state as a Request is successful
            dispatch(uiActions.showNotifications({
                open: true,
                message: 'Sent DATA to DataBase Successfully',
                type: 'success'
            }))
        };
        try {
            await sendRequest();
        } catch (err) {
            dispatch(uiActions.showNotifications({
                open: true,
                message: 'Sending request failed',
                type: 'error'
            })
            );
        }
    }
}

1.4 App.js. Call the use Effect with a condiction so it will not loop forever:
 useEffect(() => {
    if (isFirstRender) {
      isFirstRender = false;
      return;
    }
    if (cart.changed) {
      dispatch(sendCartData(cart));
    }
  }, [cart, dispatch])// By puting the cart  and disppatch as dependencies in the useEffect. it will update everytime we change the state (cart) and an action is dispatched.
  * I need to create another state in cart-slice with initial state as false and change to true everytime we call the reducers (addToCart, removeFromCart)

# 5. useEffect to FETCH data from the store. Nikhil shopping cart app

export const fetchData = () => {
    return async (dispatch) => {
        const fectchHandler = async () => {
            const res = await fetch('https://api-shoppingcart-default-rtdb.firebaseio.com/cartItems.json');
            const data = await res.json();
            return data
        }
        try {
            const cartData = await fectchHandler();
            dispatch(cartActions.replaceData(cartData))
        } catch (err) {
            dispatch(uiActions.showNotifications({
                open: true,
                message: 'Sending request failed',
                type: 'error'
            })
            );
        }
    }
}
dispatch(cartActions.replaceData(cartData)). This will dispatch an action to a reducer that will update the data that will display in the DOM

App.js. Call a another useEffect
  useEffect(() => {
    dispatch(fetchData())
  }, [dispatch])