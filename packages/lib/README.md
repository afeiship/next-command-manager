# react-command-manager
> React command manager.

## installation
```shell
yarn add @jswork/react-command-manager
```

## usage

> 1. Add provider to root. 
```jsx
import React from 'react';
import ReactDOM from 'react-dom/client';
import { scanVite } from '@jswork/scan-modules';
import ReactCommandManager from '@jswork/react-command-manager/src/main';

const moduleFiles = import.meta.glob('./shared/commands/**/*.ts', { eager: true });
const modules = scanVite(moduleFiles, {
  modules: '/commands/',
});

import App from './app';
import './index.scss';

ReactDOM.createRoot(document.getElementById('root')!).render(
  <ReactCommandManager modules={modules} debug>
    <App />
  </ReactCommandManager>,
);
```

> 2. define a command
```jsx
import { defineCommand } from '@jswork/react-command-manager';

export default defineCommand({
  methods: {
    init(){
      console.log('init posts will execute at first time');
    },
    create() {
      console.log('create posts');
    },
    update({ title }) {
      console.log('update post', title);
    },
  },
});
```

## 3. execute a command
```jsx
<button onClick={() => nx.$exec('posts.create')}>Create</button>
```