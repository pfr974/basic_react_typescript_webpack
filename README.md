# Setting up a React + Typescript project with webpack

This is simply to keep track of the steps I took to set up a React + Typescript project with webpack following [Learn React with TypeScript](https://www.packtpub.com/product/learn-react-with-typescript-second-edition/9781804614204) by Carl Rippon.

## Webpack

Webpack is a tool that "bundles JavaScript files for usage in a browser". As far as I understand this means that it takes all the files necessary for a project to run and group them together so that they can be used in a browser. I guess this is useful knowing that we are going to use React and Typescript and will probably deal with various files of different format.

## Setting up the project

We are going to start by setting up a `src` folder to hold our source code and write the various configuration files that we place at the root of the project folder. 

We start first with a `package.json` file at the root level and a simple `index.html` HTML file in the `scr` folder:

```json
{
  "name": "my-app",
  "description": "My first React and TypeScript app",
  "version": "0.0.1",
}
```

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8" />
    <title>My app</title>
  </head>
  <body>
    <div id="root"></div>
    <p> Hello World!</p>
  </body>
</html>
```
Nothing dramatic for now. The next thing to is to install Typescript and React in the project via `npm`:
  
```bash
npm install --save-dev typescript
```

With Typescript after running the `npm` command, we also have to create a configuration file, `tsconfig.json` at, you guess it, the root of the project. To be completely honest, I still struggle to understand the content of this file:

```json
{
  "compilerOptions": {
    "noEmit": true,
    "lib": [
      "dom",
      "dom.iterable",
      "esnext"
    ],
    "moduleResolution": "node",    
    "allowSyntheticDefaultImports": true,
    "esModuleInterop": true,
    "jsx": "react",
    "forceConsistentCasingInFileNames": true,
    "strict": true
  },
  "include": ["src"],
  "exclude": ["node_modules", "dist"]
}
```
From my memory of my previous job, I would say that since we are going to have files with the `.tsx` extension, we need to configure how the Typescript compiler will handle them. We also need to tell it that we are going to use React in this project so that's where the `"jsx": "react"` is coming from.

Now for React, while we do need to use `npm`, it requires slightly more command lines:
  
  ```bash
  npm install react react-dom
  npm install --save-dev @types/react @types/react-dom
  ```

  The first line installs React and React-DOM. `react` is the main library and `react-dom` is needed for web appplications. With the former, I have just realised that it's actually in its name after reading about the DOM concept in my Javascript course...

  At this point, it's also interesting to point out that while we run these `npm` commands, our `package.json` file is being updated:

  ```json
  {
  "name": "my-app",
  "description": "My first React and TypeScript app",
  "version": "0.0.1",
  "devDependencies": {
    "@types/react": "^18.2.55",
    "@types/react-dom": "^18.2.19",
    "typescript": "^5.3.3"
  },
  "dependencies": {
    "react": "^18.2.0",
    "react-dom": "^18.2.0"
  }
}
```

To finish adding React, we also need an `index.tsx` file in the `src` folder:

```tsx
import React, { StrictMode } from 'react';
import { createRoot } from 'react-dom/client';

const root = createRoot(
  document.getElementById('root') as HTMLElement
  );

function App() {
  return <h1>My FIRST React and TypeScript App!</h1>;
}

root.render(
  <StrictMode>
    <App />
  </StrictMode>,
);
```

As I understand it, this file is complementary to the `index.html` file. In the static html file, we have a way to reach out to React via `<div id="root"></div>`. In the `tsx` file, we define a constant `root`. To define this constant, we start by looking for the `root` id in our html file via `document.getElementById`. React is then "used" via the `createRoot` function that we have imported a few line above. `createRoot` load the React component, defined by the `App` function into the `root`constant. Here, our React component is simply a `h1` tag with a `"My FIRST React and TypeScript App!"` message. 

We could have just put that tag into our static HTML file, but why do simple when we can do complicated? In more seriousness, this is a bit overdone here, but I am starting to get it now.


