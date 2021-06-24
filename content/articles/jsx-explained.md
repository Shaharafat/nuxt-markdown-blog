---
title: JSX Explained
description: JSX is JavaScript Extension Syntax. It is used in react to write markup and JavaScript together easily. Today, in this blog I will try to cover all JSX thing you should know. 
author:
  name: Shah Arafat
  image: /_nuxt/assets/images/arafat.jpg
  designation: Frontend Developer
---
JSX is JavaScript Extension Syntax. It is used in react to write markup and JavaScript together easily. Today, in this blog I will try to cover all JSX thing you should know. 

Before JSX, when we need to create any react element, we used the `React.createElement()`.

```js
// Syntax: React.createElement(component, props, ...children);

var RootElement = React.createElement(
"div", null, 
React.createElement("h1", { style: { color: red } }, "The world is yours"), 
React.createElement("p", null, "Say hello to my little friend")
);
```

In the example above, we created a react element using `React.createElement()`. It has a container div, inside the div it has two elements `h1` and `p`. `h1` element has a style to set the colour to red and both the element has some text inside.

This isn't easy to write HTML type of markup this way. To make this thing easier facebook came up with JSX. 

Using JSX you can create react element by writing markup like HTML. Behind the scene, JSX will be converted to plain javascript using the package [Babel](https://babeljs.io/). With JSX we can create the above element this way.

```js
const RootElement = (
  <div>
    <h1 style={{color: red}}>The world is yours</h1>
    <p>Say hello to my little friend</p>
  </div>
)
```

You can paste the code [here](https://babeljs.io/repl) and see the output on the right side, which is pretty much the same we wrote using `React.createElement()`.

#Expressions in JSX
You can write any JavaScript expression in JSX. Any expression you put inside JSX. It must be wrapped using curly braces `{}`. 

```js
const language = 'JavaScript';

const element = <h1>Hello there, I am learning {language}</h1>;

ReactDOM.render(
  element,
  document.getElementById('root')
);
```

Here we injected the value of the variable 'language' inside h1 element. 

> If your expression inside JSX returns an object. It will throw an error. 

Remember, You can use any valid JS expression inside JSX. You can't use `if else` condition inside JSX. Rather, you can use the ternary operator to make a decision.
```js

const App = () =>{
  const [isDisabled, setIsDisabled] = useState(false);

  return (
       <button disabled={isDisabled ? true : false}>Simple Button</button>
  );

}
```

Look, we used the ternary operator to make but button disable or enable. If you try to use the `if else` statement here. I will not work.

#class in JSX
Though JSX looks almost similar to HTML. But there are some changes. 
If you want to use CSS class in your JSX, you might use `class=""`. But it's not that ideal way in JSX. You should use `className=""` instead.

#Empty tag in JSX
If you have an empty tag in JSX like `img` tag. You must close it with `/>` like XML. 

```js
const image = <img src={url} />;
```

#Multiple elements in JSX


```js
const App = () =>{
  
  return (
       <>
         <h1>Hey there, This is Arafat.</h1>
         <img src={url} />
       </>
  );

}
```

If you have multiple elements in JSX. You must wrap all element with a root element. It can be a `<div>` element or using `React.Fragment` element. You can use `<></>` as an alternative to React.Fragment.

#Props in JSX
You can pass JavaScript expressions as props in JSX. 

```js
return (
       <Component foo={ 1 + 2 + 3 + 4 } >
         <h1>Hey there, This is Arafat.</h1>
         <img src={url} />
       </Component>
  );
```
#Default props value
If pass no value to the props it defaults to true. 
```js

const App = () =>{

  return (
       <button disabled></button>
  );

}
```

In the example above, the button element has an attribute `disabled`. But we didn't pass any value for this. That's why by default its value is `true`.

#### Some other resources : [JSX Basics](https://reactjs.org/docs/introducing-jsx.html) [JSX in depth](https://reactjs.org/docs/jsx-in-depth.html)

With all that being said, I highly recommend you keep learning. 

Thank you for reading my blog. Feel free to connect on [Linkedin](https://www.linkedin.com/in/shah-arafat/) and [Twitter](https://twitter.com/sharafhat)
