### Day 1: Basics of React

- What is Component
- Component Syntax
- Creating First Component
- Components Challenges
- Multiple Components
- Multiple Components Challenge

<br/>

# React

- React is a JavaScript library for building user interfaces.
- It is created by Facebook and is used to build web applications.
- React is a component-based framework that allows you to create reusable UI elements.

# How to Setup vite with React

- Install Node.js and npm: Visit nodejs.org to download and install Node.js.
- Create a new project directory and navigate to it.
- Run `npm create vite@latest` to create a new project.
- give project name
- select React
- select javascript
- cd to move to project directory
- Run `npm install` to install dependencies.
- Run `npm run dev` to start the development server.

# What is Component

- Components are the building blocks of React applications.
- They are functions that return JSX (JavaScript XML) that represents the UI.
- Components can be reused across the application and can be nested to create complex UIs.

# Component Syntax

- Create a new file in the `src` directory and name it `App.js`.

```jsx
function App() {
  return (
    <div>
      <h1>Hello, world!</h1>
      <p>This is a React component.</p>
    </div>
  );
}
```

# Creating First Component

#### Steps : Create a `Greet` Component

1. Create a new file called `Greet.jsx`.
2. Inside this file, create a functional component named `Greet`.
3. The `Greet` component should return a `<div>` element with the following:
   - A `<h1>` element with the text `"Welcome to My Website!"`
   - A `<h1>` element with the text `"This is my first React component."`

### Answer Available in problem1 (Greet.jsx) file.

# Components Challenges

1. Create a new file called `Students.jsx`.
2. Inside this file, create a functional component named `Students`.
3. The `Students` component should return a `<div>` element with the following:
   - A `<h1>` element with the text `"Name : Rahda"`
   - A `<h1>` element with the text `"Age : 22"`

### Answer Available in problem2 (Students.jsx) file.

# Multiple Components

- For large website we have to create multiple components and these are stored in `Components` folder.
- We can create multiple components in a single file.

# Multiple Components Challenge

- view task.md file.
