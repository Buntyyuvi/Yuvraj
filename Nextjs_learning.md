

## **Concepts:**



1. If you want to use Navbar.js inside pages/index.js, you do:



**import Navbar from "../components/Navbar";**





2\) **import styles from "./Navbar.module.css";**

&nbsp; 

This is the magic of CSS Modules in Next.js (and React in general).

Let me explain step by step:



🔍 What happens when you write this?

Navbar.module.css is a CSS Module file.



The .module.css extension tells Next.js:

👉 “Hey, treat this CSS as scoped styles for this component only.”



When you import styles from "./Navbar.module.css";



Next.js compiles that CSS file into a JavaScript object called styles.



**Example: if your CSS file looks like this:**

.nav {

&nbsp; background: black;

}



.navList {

&nbsp; display: flex;

}



**Next.js will internally turn it into something like:**



{

&nbsp; nav: "Navbar\_nav\_\_a1b2c", 

&nbsp; navList: "Navbar\_navList\_\_x9y8z"

}

**(It automatically generates unique class names, so they don’t clash with other components’ CSS.)**



<nav className={styles.nav}></nav>



**It will render in HTML as:**

<nav class="Navbar\_nav\_\_a1b2c"></nav>





**Why is this good?**



✅ Scoped Styles → CSS won’t leak into other components.



✅ No Naming Conflicts → Each class gets a unique hash (like Navbar\_nav\_\_a1b2c).



✅ Cleaner Code → You can safely use simple class names (.nav, .title) in every component without worrying about overlap.





##### Great example of how to make a POST request from your frontend to a Next.js API route.



"use client"



export default function Home() {

&nbsp; const handleClick = async ()=>{

&nbsp; let data = {

&nbsp;   name: "Yuvi",

&nbsp;   status : "Billionare"

&nbsp; }

&nbsp;   let a = await fetch("api/",{method:"POST", headers:{

&nbsp;     "Content-Type":"application/json"

&nbsp;   },

&nbsp;   body: JSON.stringify(data),

&nbsp; })

&nbsp; let res  = await a.json()

&nbsp; console.log(res)

&nbsp; }

&nbsp; return (

&nbsp;  <div>

&nbsp;   <h1 className="text xl font-bold"> This Next.js Api Routes</h1>

&nbsp;   <button onClick={handleClick}>Click Me</button>

&nbsp;  </div>

&nbsp; );

}



###### **Explaination** :



**export default function Home() {}**

This defines your Home page component.

Since this is in pages/index.js, this is your / (root) route.



**const handleClick = async () => {}**

This is an event handler that runs when you click the button.

It is marked async so you can use await inside (for async operations like fetching data).



**2️⃣ Creating Data to Send**

let data = {

&nbsp; name: "Yuvi",

&nbsp; status: "Billionare"

}



You are creating a JavaScript object with two keys:

{ name: "Yuvi", status: "Billionare" }



This is the data you will send to your API.



**3️⃣ Fetch API Call**



let a = await fetch("api/", {

&nbsp; method: "POST",

&nbsp; headers: {

&nbsp;   "Content-Type": "application/json"

&nbsp; },

&nbsp; body: JSON.stringify(data),

})



🔑 Key Points:

✅ fetch("api/", ...)

Calls /api/ route in your Next.js app (you must have a file like pages/api/index.js to handle it).

✅ method: "POST"

This tells the server we are sending data (not just fetching).

✅ headers

"Content-Type": "application/json" tells the server:

"Hey! I'm sending JSON data."

✅ body: JSON.stringify(data)

You must convert the JavaScript object into a JSON string before sending.

Example: {"name":"Yuvi","status":"Billionare"}

✅ await

Waits until the server sends a response, then stores it in a.



**4️⃣ Converting Response to JSON**

let res = await a.json()

console.log(res)



a.json() converts the response into a JavaScript object.

Then console.log(res) prints it in your browser console.

##### 













