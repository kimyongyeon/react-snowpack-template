# 관련 링크 
https://www.vectorlogo.zone/logos/reactjs/
https://www.snowpack.dev/tutorials/react


# 시작방법 
npx create-snowpack-app react-snowpack --template @snowpack/app-template-minimal

cd react-snowpack
npm run start

npm install react react-dom --save

# 파일 이름 바꾸기 
mv index.js index.jsx

# index.jsx
/_ Add JavaScript code here! _/
import React from 'react';
import ReactDOM from 'react-dom';
ReactDOM.render(<div>"HELLO REACT"</div>, document.getElementById('root'));

# index.html 
```
<body>
   <div id="root"></div>
   <script type="module" src="/index.js"></script>
</body>
```

# 파일 이동 및 폴더생성 
mkdir src
mkdir public
mv index.jsx src/index.jsx
mv index.html public/index.html
mv index.css public/index.css

# snowpack.config.js 파일 수정
```
  mount: {
   // directory name: 'build directory'
   public: '/',
   src: '/dist',
  },
```  

# index.html 변경
```
<body>
   <h1>Welcome to Snowpack!</h1>
   <div id="root"></div>
   <script type="module" src="/dist/index.js"></script>
</body>
```

# App.jsx 
```
import React, { useState, useEffect } from 'react';

function App() {
  // Create the count state.
  const [count, setCount] = useState(0);
  // Update the count (+1 every second).
  useEffect(() => {
    const timer = setTimeout(() => setCount(count + 1), 1000);
    return () => clearTimeout(timer);
  }, [count, setCount]);
  // Return the App component.
  return (
    <div className="App">
      <header className="App-header">
        <p>
          Page has been open for <code>{count}</code> seconds.
        </p>
      </header>
    </div>
  );
}

export default App;
```

# index.jsx
```
import React from 'react';
import ReactDOM from 'react-dom';
import App from './App.jsx';
ReactDOM.render(
    <React.StrictMode>
        <App />
    </React.StrictMode>,
    document.getElementById('root'),
);
```

# App.jsx
```
  
 import logo from './logo.svg';

  function App() {
    // Create the count state.
    const [count, setCount] = useState(0);
    // Create the counter (+1 every second).
    useEffect(() => {
      const timer = setTimeout(() => setCount(count + 1), 1000);
      return () => clearTimeout(timer);
    }, [count, setCount]);
    // Return the App component.
    return (
      <div className="App">
        <header className="App-header">
       <img src={logo} className="App-logo" alt="logo" />
        <p>
```

# App.css
```
.App {
  text-align: center;
}

.App p {
  margin: 0.4rem;
}

.App-logo {
  height: 40vmin;
}

@media (prefers-reduced-motion: no-preference) {
  .App-logo {
    animation: App-logo-spin infinite 20s linear;
  }
}

.App-header {
  background-color: #282c34;
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  font-size: calc(10px + 2vmin);
  color: white;
}

@keyframes App-logo-spin {
  from {
    transform: rotate(0deg);
  }
  to {
    transform: rotate(360deg);
  }
}
```

# App.jsx
```
import logo from './logo.svg';
import './App.css';
```

# index.jsx
```
ReactDOM.render(
    <React.StrictMode>
        <App />
    </React.StrictMode>,
    document.getElementById('root'),
);
// Hot Module Replacement (HMR) - Remove this snippet to remove HMR.
// Learn more: https://www.snowpack.dev/concepts/hot-module-replacement
if (import.meta.hot) {
  import.meta.hot.accept();
}
```

# fast-refresh 설정
```
npm install @snowpack/plugin-react-refresh --save-dev
```

# snowpack.config.js
```
module.exports = {
    mount: {
        public: '/',
        src: '/dist',
    },
    plugins: ['@snowpack/plugin-react-refresh'],
};
```


