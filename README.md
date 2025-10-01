<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Redux Toolkit Notes</title>
  <link href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;500;700&family=Poppins:wght@300;400;600&display=swap" rel="stylesheet" />
  <style>
    body {
      font-family: 'Roboto', sans-serif;
      margin: 0;
      padding: 0;
      background: #f7f9fc;
      color: #333;
      display: flex;
      justify-content: center;
      align-items: flex-start;
      flex-direction: column;
      min-height: 100vh;
      overflow-x: hidden;
      transition: all 0.3s ease;
    }

    /* Dark mode styles */
    body.dark-mode {
      background: #121212;
      color: #f7f7f7;
    }

    h1 {
      font-size: 2.5rem;
      color: #8d8d96;
      font-family: 'Poppins', sans-serif;
      font-weight: 600;
      padding: 30px 20px;
      display: flex;
      justify-content: center;
      align-items: center;
      text-align: center;
      margin: 0 auto;
    }

    .container {
      background-color: #ffffff;
      padding: 40px;
      border-radius: 10px;
      width: 90%;
      max-width: 1200px;
      box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1);
      color: #333;
      margin: 0 auto;
      transition: all 0.3s ease;
    }

    body.dark-mode .container {
      background-color: #333;
      color: #f7f7f7;
    }

    .section {
      margin-bottom: 40px;
    }

    .section h2 {
      color: #444;
      font-size: 1.6rem;
      margin-bottom: 15px;
      font-weight: bold;
      border-bottom: 2px solid #007bff;
      padding-bottom: 5px;
    }

    body.dark-mode .section h2 {
      color: #f7f7f7;
      border-bottom: 2px solid #007bff;
    }

    .note {
      margin-top: 10px;
      font-size: 1.1rem;
      color: #555;
    }

    body.dark-mode .note {
      color: #f7f7f7;
    }

    .code-block {
      background-color: #f5f5f5;
      padding: 20px;
      border-radius: 8px;
      border-left: 5px solid #007bff;
      font-family: 'Courier New', monospace;
      font-size: 1rem;
      color: #333;
      margin-top: 20px;
      position: relative;
      transition: all 0.3s ease;
    }

    body.dark-mode .code-block {
      background-color: #706666;
      color: #f7f7f7;
    }

    .code-block:hover {
      box-shadow: 0 8px 20px rgba(0, 0, 0, 0.1);
      transform: scale(1.02);
    }

    .copy-btn {
      background-color: #000000;
      color: #fff;
      padding: 12px 24px;
      border: none;
      border-radius: 5px;
      font-size: 1.1rem;
      cursor: pointer;
      position: absolute;
      top: 10px;
      right: 10px;
      transition: background-color 0.3s ease, transform 0.3s ease;
    }

    .copy-btn:hover {
      background-color: #007bff;
      transform: scale(1.05);
    }

    .copy-btn:active {
      transform: scale(0.95);
    }

    .copied-btn {
      background-color: #007bff !important;
    }

    pre {
      background-color: #333;
      color: #f7f7f7;
      padding: 15px;
      border-radius: 10px;
      font-size: 1.1rem;
      overflow-x: auto;
    }

    ul {
      list-style-type: square;
      margin-left: 20px;
      font-size: 1rem;
      color: #555;
    }

    body.dark-mode ul {
      color: #f7f7f7;
    }

    .filename {
      font-size: 1.2rem;
      font-weight: bold;
      color: #c5daf0;
      margin-top: 10px;
    }

    body.dark-mode .filename {
      color: #007bff;
    }

    /* Add some spacing between sections */
    .section + .section {
      margin-top: 40px;
    }

    /* Mobile responsiveness */
    @media (max-width: 768px) {
      h1 {
        font-size: 1.8rem;
      }

      .container {
        padding: 20px;
        width: 100%;
        max-width: 100%;
      }

      .section h2 {
        font-size: 1.4rem;
      }

      .note,
      .filename,
      .code-block {
        font-size: 1rem;
      }

      pre {
        font-size: 1rem;
      }

      .copy-btn {
        font-size: 1rem;
        padding: 10px 20px;
      }

      .section {
        margin-bottom: 20px;
      }
    }

  </style>
</head>

<body>
    <h1>Redux Toolkit Notes</h1>

    <button id="theme-toggle" style="position: sticky; z-index: 1000; top: 20px; left: 9999px; background-color: #007bff; color: white; padding: 10px 15px; border: none; cursor: pointer; border-radius: 5px; font-weight: 700;">dark mode</button>

    <div class="container">
      <h1>Redux Toolkit</h1>
      <h2>Introduction</h2>
      <p class="note">
        Redux Toolkit provides a set of tools and best practices for efficient Redux development.
      </p>
      <!-- Section 1 -->
      <div class="section">
        <h2>1. What is Redux Toolkit?</h2>
        <p class="note">
          Redux Toolkit is the official, recommended way to use Redux in modern JavaScript apps. It simplifies store setup and reduces boilerplate, allowing developers to focus on building apps rather than managing state.
        </p>
      </div>

      <!-- Section 2 -->
      <div class="section">
        <h2>2. Installation</h2>
        <pre><code>npm install @reduxjs/toolkit react-redux</code></pre>
      </div>

      <!-- Section 3 -->
      <div class="section">
        <h2>3. Folder Structure</h2>
        <pre><code>
src/
├── redux/
│   ├── store.js
│   └── features/
│       └── counter/
│           ├── counterSlice.js
│           └── Counter.jsx
        </code></pre>
      </div>

      <!-- Section 4 -->
      <div class="section">
        <h2>4. Creating the Slice</h2>
        <p class="filename">📄 src/redux/features/counter/counterSlice.js</p>
        <div class="code-block">
          <pre><code id="code1">import { createSlice } from '@reduxjs/toolkit';

const initialState = { value: 0 };

export const counterSlice = createSlice({
  name: 'counter',
  initialState,
  reducers: {
    increment: (state) => {
      state.value += 1;
    },
    decrement: (state) => {
      if (state.value > 0) {
        state.value -= 1;
      }
    },
    incrementByAmount: (state, action) => {
      state.value += action.payload;
    }
  }
});

export const { increment, decrement, incrementByAmount } = counterSlice.actions;
export default counterSlice.reducer;</code></pre>
          <button class="copy-btn" onclick="copyCode('code1', this)">Copy Code</button>
        </div>
      </div>

      <!-- Section 5 -->
      <div class="section">
        <h2>5. Setting Up the Store</h2>
        <p class="filename">📄 src/redux/store.js</p>
        <div class="code-block">
          <pre><code id="code2">import { configureStore } from '@reduxjs/toolkit';
import counterReducer from './features/counter/counterSlice';

export const store = configureStore({
  reducer: {
    counter: counterReducer,
  },
});</code></pre>
          <button class="copy-btn" onclick="copyCode('code2', this)">Copy Code</button>
        </div>
      </div>

      <!-- Section 6 -->
      <div class="section">
        <h2>6. Wrapping the App with Provider</h2>
        <p class="filename">📄 src/main.jsx</p>
        <div class="code-block">
          <pre><code id="code3">import React from 'react';
import ReactDOM from 'react-dom/client';
import { Provider } from 'react-redux';
import { store } from './redux/store';
import App from './App';

ReactDOM.createRoot(document.getElementById('root')).render(
  &lt;React.StrictMode&gt;
    &lt;Provider store={store}&gt;
      &lt;App /&gt;
    &lt;/Provider&gt;
  &lt;/React.StrictMode&gt;
);</code></pre>
          <button class="copy-btn" onclick="copyCode('code3', this)">Copy Code</button>
        </div>
      </div>

      <!-- Section 7 -->
      <div class="section">
        <h2>7. Counter Component</h2>
        <p class="filename">📄 src/redux/features/counter/Counter.jsx</p>
        <div class="code-block">
          <pre><code id="code4">import React, { useState } from 'react';
import { useSelector, useDispatch } from 'react-redux';
import { increment, decrement, incrementByAmount } from './counterSlice';

export function Counter() {
  const count = useSelector((state) => state.counter.value);
  const dispatch = useDispatch();
  const [inputValue, setInputValue] = useState(0);

  return (
    &lt;div&gt;
      &lt;button aria-label="Increment value" onClick={() =&gt; dispatch(increment())}&gt;
        Increment
      &lt;/button&gt;
      &lt;h1&gt;{count}&lt;/h1&gt;
      &lt;button aria-label="Decrement value" onClick={() =&gt; dispatch(decrement())}&gt;
        Decrement
      &lt;/button&gt;

      &lt;input
        type="number"
        value={inputValue}
        onChange={(e) =&gt; setInputValue(e.target.value)}
      /&gt;
      &lt;button onClick={() =&gt; dispatch(incrementByAmount(Number(inputValue)))}&gt;
        Add Amount
      &lt;/button&gt;
    &lt;/div&gt;
  );
}</code></pre>
          <button class="copy-btn" onclick="copyCode('code4', this)">Copy Code</button>
        </div>
      </div>

      <!-- Section 8 -->
      <div class="section">
        <h2>8. Testing the Application</h2>
        <ul>
          <li>Run the app and test the counter functionality.</li>
          <li>Make sure the increment, decrement, and add amount functionalities work as expected.</li>
        </ul>
      </div>
    </div>

    <script>
      function copyCode(id, button) {
        const code = document.getElementById(id).textContent;
        navigator.clipboard.writeText(code);
        button.classList.add('copied-btn');
        button.textContent = 'Copied!';
        setTimeout(() => {
          button.classList.remove('copied-btn');
          button.textContent = 'Copy Code';
        }, 1500);
      }

      // Toggle dark mode
      document.getElementById('theme-toggle').addEventListener('click', () => {
        document.body.classList.toggle('dark-mode');
        const isDarkMode = document.body.classList.contains('dark-mode');
        document.getElementById('theme-toggle').textContent = isDarkMode ? 'Light Mode' : 'Dark Mode';
      });
    
    </script>
</body>
</html>
<!-- ye notes hain -->
