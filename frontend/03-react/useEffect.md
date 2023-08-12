## useEffect

1. useEffect as a custom hook for fetching data. The Net Ninja blog app
2. Post data. The Net Ninja blog app
* In the tutorial this works ok but when I tried in Song Gaver app it didn't updated the DOM so as return I used a javascrip code to refresh the page. This is not the way it should be. I believe is better to add a dependency to useFetch to it will fire a action everytime the data change
3. useEffect to PUT data. Nikhil shopping cart app

----------------------------------------------------------
# The Net Ninja blog app in Mac:
/Users/carlosinfante/Desktop/coding-projects/winc-academy/frontend-course/MODULE9 - DEBUGGING and DOMAIN MODELING/REVIEW/react-hooks/useState nd useEffect/The_Net_Ninja-blog-app

# The Net Ninja blog app in GitHub:
https://github.com/carloscfgos1980/React-useState-useEffect-blog

---------------------------------------------------------
# 1. useEffect as a custom hook for fetching data. The Net Ninja blog app 
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
# Nikhil shopping cart app in Mac:
/Users/carlosinfante/Desktop/coding-projects/winc-academy/frontend-course/MODULE9 - DEBUGGING and DOMAIN MODELING/REVIEW/redux/tutorials/2. NoAPI/Redux-Shopping-Cart-App-Nikhil

# Nikhil shopping cart app in Github:
https://github.com/carloscfgos1980/React-Redux-toolkit-shoppingCart-Api_I

-------------------------------------------------------------------------

* Nikhil use Notificatioins which make the PUT action fuction a lot more ecomplex. Explanation tutorial video from 1:13 to 1:28 hr:
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