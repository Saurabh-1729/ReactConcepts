Great question! In React, **cleanup functions** in `useEffect` are used to prevent memory leaks and unwanted side effects by "cleaning up" after the effect runs. Here’s how you decide when and why to use them:

---

## **When Should You Perform Cleanup in useEffect?**

You should add a cleanup function to your `useEffect` **whenever your effect:**

1. **Sets up a subscription or listener**
   - e.g., event listeners, WebSocket connections, timers, intervals, or external data subscriptions.
2. **Initiates an asynchronous operation that may complete after the component is unmounted**
   - e.g., fetch requests, promises.
3. **Allocates resources that need to be released**
   - e.g., manually manipulating the DOM, using third-party libraries that require teardown.

---

## **Why is Cleanup Important?**

- **Prevents memory leaks** (e.g., leftover event listeners)
- **Avoids unwanted behaviors** (e.g., updating state on unmounted components)
- **Ensures correct app behavior** (e.g., no duplicate listeners or intervals)

---

## **How Do You Add Cleanup in useEffect?**

You return a function from your `useEffect` callback. This function will run:
- **Before the component unmounts**
- **Before the effect runs again (if dependencies change)**

**Example 1: Cleaning up an event listener**
```jsx
useEffect(() => {
  function handleResize() {
    // ...do something
  }
  window.addEventListener('resize', handleResize);

  // Cleanup function
  return () => {
    window.removeEventListener('resize', handleResize);
  };
}, []); // Empty array means the effect runs once on mount and cleans up on unmount
```

**Example 2: Cleaning up a timer**
```jsx
useEffect(() => {
  const timer = setInterval(() => {
    // ...do something
  }, 1000);

  return () => clearInterval(timer);
}, []);
```

**Example 3: Aborting a fetch request**
```jsx
useEffect(() => {
  const controller = new AbortController();

  fetch('/api/data', { signal: controller.signal })
    .then(response => response.json())
    .then(data => {/* ... */});

  return () => {
    controller.abort();
  };
}, []);
```

---

## **Summary Table**

| If your effect...                        | Add cleanup?      | Example              |
|------------------------------------------|-------------------|----------------------|
| Sets up event listeners                  | Yes               | window.addEventListener |
| Starts a timer/interval                  | Yes               | setInterval, setTimeout |
| Subscribes to external data              | Yes               | WebSocket, RxJS      |
| Manipulates the DOM directly             | Yes (often)       | third-party libraries |
| Purely fetches data and updates state    | No (usually)      | fetch, axios         |

---

**In short:**  
**Add a cleanup function if your effect sets up something that needs to be undone when the component unmounts or before the effect runs again.**

Let me know if you want more examples or have a specific scenario in mind!
