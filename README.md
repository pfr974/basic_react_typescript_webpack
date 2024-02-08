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
Nothing dramatic for now. The next thing to is to install Typescript and React in the project.