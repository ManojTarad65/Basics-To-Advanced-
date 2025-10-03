# NextJs

1. `Server Side Rendering`
2. `Static Site Generation`
3. `API Routes`
4. `Fast page rendering`
5. `Image Optimization`
6. `Seo Optimization`

# Routing or Page Navigation

- Routing gives direction to website

``` javascript
let Website Name 👉 "Example.com"
Home Page 👉 "Example.com/home"
```
# How To Create Routing

```jsx
Create a new folder in `app` folder

Step 1 : let folder name 👉 "home"
Setp 2 : Create a New file `page.js` in `home` folder
Step 3 : Write Some Code in `page.js` and it is a new page 👉 "Example.com/home"
```
# 404 Page Not Found
```jsx
If Page Not Found then it will show 404
```
# Nested Routing

```jsx
Create a new folder in `app` folder

Step 1 : let folder name 👉 "Colleges"
Setp 2 : Create another folder "Program_name" inside "Colleges" folder
Step 3 : create "page.js" inside it. 
page 👉 "Example.com/Colleges/Program_name"
```

# Link 

```
1. Link is used to navigate between pages
2. Link Make user Experience Better
```
```jsx
Step 1. import Link from "next/link"
Step 2. Use href to navigate to the page

Example 👉 <Link href="/home">Home</Link>
When 👤 click on "Home" then it will navigate to "Example.com/home"
```
```jsx
import React from "react";
import Link from "next/link";
const Navbar = () => {
  return (
    <div className="navbar">
      <div className="logo">Logo</div>
      <div className="nav">
        <div className="nav-items">
          <Link href="/">Home</Link>
          <Link href="/colleges">colleges</Link>
          <Link href="/about">About</Link>
          <Link href="/contact">Contact</Link>
        </div>
      </div>
    </div>
  );
};

export default Navbar;

```
# UseRouter

- UseRouter is same as Link but Link is used for Client Side Routing and UseRouter is used for performing multiple actions . 

```jsx
Step 1. import {useRouter} from "next/navigation"
Step 2. For some ui action use "use client"
Step 3. const router = useRouter();
Step 4. router.push("/home");
```
```jsx
"use client";
import { useRouter } from "next/navigation";
import React from "react";
const Nav = () => {
  const router = useRouter();
  const handleContactClick = () => {
    router.push("/contact");
    // other task can be executed parallelly
  };
  return (
    <div className="navbar">
      <div className="logo">Logo</div>
      <div className="nav">
        <div className="nav-items">
          <button onClick={() => router.push("/")}>Home</button>
          <button onClick={() => router.push("/colleges")}>colleges</button>
          <button onClick={() => router.push("/about")}>About</button>
          <button onClick={handleContactClick}>Contact</button>
        </div>
      </div>
    </div>
  );
};

export default Nav;
```
# Skip Page

```jsx
create a folder in side `( )` inside `app` folder

For Example 👉 (auth)/login.js
👉 "Example.com/login"
```

# Dynamic Routing

- If multiple pages have same structure then we can use dynamic routing.
- Dynamic Routing means creating a single page which can be used for multiple pages.

```jsx
Step 1. create a folder within these Brackets 👉 `[ ]` inside `app` folder
```
### [colleges] folder is made inside app folder 👇
```jsx
"use client";
import React from "react";

const Users = ({ params }) => {
  return <div className="main">{params.colleges}</div>;
};

export default Users;

```

# Catch All Routes

- Extracting all the routes from the url
```jsx
Step 1. create a folder within these Brackets 👉 `[ ...folder_name ]` inside `app` folder
```

```jsx
import React from "react";

const article = ({ params }) => {
  return (
    <div className="main flex flex-col">
      <div>All routes are excepted </div>
      <div>
        {params.article.map((item) => (
          <div
            className="bg-blue-500 p-4 m-4 rounded hover:bg-black hover:text-white"
            key={item}
          >
            <div>✅ {item}</div>
          </div>
        ))}
      </div>
    </div>
  );
};

export default article;

```

# Handling 404 Page Not Found

```jsx
Step 1. create a new file `not-found.js` inside `app` folder
```

```jsx
import React from "react";

const notFound = () => {
  return <div>404 Page Not Found</div>;
};

export default notFound;
```

# Redirect

- Redirecting to a different page
```jsx
Step 1. import { redirect } from "next/navigation";
Step 2. redirect("/home");
```

```jsx
import { redirect } from "next/navigation";
import React from "react";

const Id = ({ params }) => {
  if (params.id === "1") {
    redirect("/login");
  }
  return <div className="main">Id : {params.id}</div>;
};

export default Id;

```
# Server side Component
```jsx
By default all the components are server side components
```
```jsx
import React from "react";
console.log("Server Side Rendering");
// It will not display in the browser's console
const Home = () => {
  return (
    <div>
      <div className="main">
        <div>Home Page</div>
      </div>
    </div>
  );
};

export default Home;

```
### Error

```jsx
import React from "react";

const page = () => {
  return (
    <div>
      <button onClick={() => alert("clicked")}>click Me</button>
    </div>
  );
};
// by default it is server side component
export default page;
```

# Client side Component
```jsx
To make a component client side component use "use client"
```
```jsx
"use client";
import React from "react";
console.log("Client Side Rendering");
// It will display in the browser's console
const Home = () => {
  return <div>Home</div>;
};

export default Home;
```

# Layout

- Layout is used to create a common structure for all the pages

```jsx
For multiple pages header and footer are same which can be handled by "layout.js" file
```
### Project Structure
```jsx
/project-root
  /app
    /college
      layout.jsx
  /Components
    NavBar.jsx
    Footer.jsx
```
### layout.jsx
```jsx
import React from "react";
import NavBar from "../../Components/NavBar";
import Footer from "../../Components/Footer";
const layout = ({ children }) => {
  return (
    <div>
      <NavBar />
      {children}
      <Footer />
    </div>
  );
};

export default layout;

```
# Accessing Path form Layout
```jsx
"use client";
import { Geist, Geist_Mono } from "next/font/google";
import "./globals.css";
import NavBar from "../Components/NavBar";
import Footer from "../Components/Footer";
import { usePathname } from "next/navigation";
const geistSans = Geist({
  variable: "--font-geist-sans",
  subsets: ["latin"],
});

const geistMono = Geist_Mono({
  variable: "--font-geist-mono",
  subsets: ["latin"],
});

// ----- Metadata Cannot be used while "use client" -----

// export const metadata = {
//   title: "Create Next App",
//   description: "Generated by create next app",
// };

export default function RootLayout({ children }) {
  const pathname = usePathname();
  console.log(pathname);
  return (
    <html lang="en">
      <body
        className={`${geistSans.variable} ${geistMono.variable} antialiased`}
      >
        <NavBar />
        {children}
        <Footer />
      </body>
    </html>
  );
}

```

# Metadata

- Metadata is used to set the title and description of the page

```jsx
export const metadata = {
  title: "Create Next App",
  description: "Generated by create next app",
};
```
```jsx
import React from "react";

const page = () => {
  return <div className="main">About Page</div>;
};

export default page;

export const metadata = {
  title: "About Page",
  description: "Explain about `About Page`",
};

```

# Images in NextJs

```jsx
// Internal Image 
import React from "react";
import Image from "next/image";
import GuruJi from "../../public/Premanadji.jpg";
const page = () => {
  return (
    <div className="main">
      <div>About Page</div>
      <Image src={GuruJi} alt="Premanand ji Maharaj" height={400} width={400} />
    </div>
  );
};

export default page;

```
### External Image

```jsx
step 1. add the image `domain` in the next.config.js file
step 2. paste image url in the `Image` tag
```
```jsx
// next.config.js
/** @type {import('next').NextConfig} */
const nextConfig = {
  images: {
    domains: ["laxmienterprisespushkar.com"],
  },
};

export default nextConfig;

```

```jsx
import React from "react";
import Image from "next/image";
const page = () => {
  return (
    <div className="main flex flex-col gap-3 rounded">
      <div>About Page</div>
      <Image
        src="https://laxmienterprisespushkar.com/wp-content/uploads/2024/03/ninja-exterior-emulsion.png"
        alt="Ninja Exterior Emulsion"
        height={300}
        width={300}
      />
    </div>
  );
};

export default page;


```
# Fonts in NextJs

```jsx
import React from "react";
import { Roboto } from "next/font/google";
const roboto = Roboto({
  weight: "500",
  subsets: ["latin"],
});
const About = () => {
  return (
    <div className="main">
      <div className={roboto.className}>About Page</div>
      <div>Font with out roboto</div>
      <div className={roboto.className}>Font with roboto</div>
    </div>
  );
};

export default About;

```

# Backend in NextJs

```jsx
/project-root
  /app
    /api
      /users
        route.js
```
```jsx
step 1. Create a folder `api` in the `app` directory
step 2. Create a file `route.js` in the `api` folder
```

# GET Request
- GET Request is used to fetch data from the server
```jsx
import { NextResponse } from "next/server";
export function GET() {
  return NextResponse.json({ user: "Radha" });
}
```
# Dynamic Routes with Api

```jsx
import { NextResponse } from "next/server";
export function GET(_, responce) {
  const id = responce.params.id;
  return NextResponse.json({ id }, { status: 200 });
}
```

# Working With Database

```jsx
/project-root
  /app
    /utils
      /db.js
```

```jsx
import { NextResponse } from "next/server";
import { users } from "../../utils/db";
export function GET() {
  return NextResponse.json({ user: users });
}
```

# Middleware

```jsx
/project-root
  /app
/middleware.js
```
```jsx
1. Authentication & Authorization → Protect specific pages/routes.
2. Redirection → Redirect users based on conditions (e.g., logged-in status).
3. Logging & Analytics → Track user activity.
4. Geo-based Content → Show content based on the user’s location.
5. Modifying Requests & Responses → Add custom headers, cookies, etc.
```

```jsx
import { NextResponse } from "next/server";

export function middleware(req) {
  if (req.nextUrl.pathname.startsWith("/colleges/program_name")) {
    return NextResponse.redirect(new URL("/about", req.url));
  }
  return NextResponse.next();
}

export const config = {
  matcher: ["/colleges/program_name"],
};

```

# Environment Variables

```jsx
/project-root
  /app
/.env.local
```

- Sensitive information like API keys, passwords, etc. should be stored in the `.env.local` file.

# POST Request
- post is used to send data to the server
```jsx
/project-root
  /app
    /api
      /users
        route.js
```
```jsx
import { NextResponse } from "next/server";
export async function POST(req) {
  const body = await req.json();
  console.log(body);
  return NextResponse.json({ success: "Data Sent Successfully" });
}
```
### Download Postman

- Download Postman from [here](https://www.postman.com/downloads/)

```jsx
// if response is not given by user then error is shown 
import { NextResponse } from "next/server";
export async function POST(req) {
  const { name, email, phone } = await req.json();
  if (!name || !email || !phone) {
    return NextResponse.json(
      { error: "Please provide name, email, and phone" },
      { status: 400 }
    );
  }
  console.log({ name, email, phone });
  return NextResponse.json({ success: "Data Sent Successfully" });
}

```
# Parallel Routes 
- Parallel routes are used to create multiple routes for a single page.
- problem without parallel routes -> you cannot use the error.tsx or loading.tsx file in the parent directory(components)
- solution -> use parallel routes , Error and loading components are used to show error and loading states. in a specific page , box will be shown . it will not show in any other page.
```jsx

// always use @ symbol for parallel routes
1. Create a folder `@members` in the `app` directory
2. Create a folder `@comments` in the `app` directory


layout.tsx
```tsx
import "./globals.css";
import { ReactNode } from "react";

type CP ={
  children : ReactNode; // main content
  members : ReactNode; // members content -> @members -> It will show all the members
  comments : ReactNode; // comments content -> @comments -> It will show all the comments
}

// members and comments are parallel routes
const RootLayout =({children, members, comments}:CP)=>{

  return (
    <html lang="en">
      <body>
        <h1>{children}</h1>
      <div className="flex">

        {/* members and comments are parallel routes */}
        {members}
        {comments}
      </div>
      
      </body>
    </html>
  );
}
export default RootLayout;

```






Project Parallel Routes -> Music Player 

# Intercepting Routes
- Intercepting routes are used to intercept the requests and responses.
- It means it will intercept the requests and responses before they reach the server.
- It helps when we click on any routing then it gives a pop up like page, but when we refresh the page then it will show that page.

```jsx
 // If you use intercepting routes then always use (.)FileName 
 // Example -> (.)ecommerce
 // (.) -> It will helps you to give pop up like page, there is a condition of using intercepting routes that is you have to create every folder which you want to use the intercepting routes. 
 // example -> (.)ecommerce then you have to create a ecommerce folder 
 // example2 -> (.)music then you have to create a music folder
```


# Client vs Server components
- Client components are used to render components on the client side.
- Server components are used to render components on the server side.
- If you want to use client components then always use "use client".
- In next js by default all the components are server components.
- Server components are used to fetch data from the server, backend,private info.
- Client components are used to render components on the client side, frontend,public info.

# Fetching Data from client side

```jsx
"use client";
import React, { useEffect, useState } from "react";

const Contact = () => {
  const [product, setProduct] = useState([]);
  useEffect(() => {
    const fetchProduct = async () => {
      const response = await fetch("https://fakestoreapi.com/products");
      const data = await response.json();
      setProduct(data);
    };
    fetchProduct();
  }, []);
  return (
    <div>
      <h1 className="text-3xl font-bold mb-8 text-center mt-8">Contact</h1>
      <ul>
        {product.map((item) => (
          <li className="p-2 border border-gray-700 rounded mb-2" key={item.id}>
            {item.title}
          </li>
        ))}
      </ul>
    </div>
  );
};

export default Contact;

```
# Fetching Data from server side

```jsx
import React from "react";
async function getData() {
  const res = await fetch("https://jsonplaceholder.typicode.com/posts");
  return res.json();
}
const Contact = async () => {
  const products = await getData();
  return (
    <div>
      {products?.map((product) => (
        <div
          key={product.id}
          className="border p-4 m-4 border-gray-200 rounded-lg shadow-md"
        >
          <h1 className="font-bold text-2xl">Title : {product.title}</h1>
          <p>Body : {product.body}</p>
        </div>
      ))}
    </div>
  );
};

export default Contact;
```

# Prisma
- Prisma is a database tool that helps you to create, manage, and interact with your database.
- It uses typescript or javascript to create a database.
- It is a ORM (Object Relational Mapping) tool.

1. npm init -y 
2. npm i typescript ts-node @types/node -D
3. npx tsc --init
4. npm i prisma -D
5. npx prisma init --datasource-provider sqlite
6. npx prisma migrate dev --name init
7. using this command to run the prisma :  npx prisma studio

Prisma Client - > It is a database client that helps you to interact with your database in a simple and efficient way.

Prisma Studio - > It is a database studio that helps you to manage your database in a simple and efficient way.

Prisma Migrate - > It is a database migration tool that helps you to manage your database schema in a simple and efficient way.


# First Backend Project

```jsx
/project-root
  /app
    /api
      /users
        route.js
```
```jsx
import { NextResponse } from "next/server";
export async function POST(req) {
  const { name, password, mobile } = await req.json();
  if (!name || !password || !mobile) {
    return NextResponse.json(
      { error: "Please provide name, password, and mobile", ok: false },
      { status: 400 }
    );
  }
  console.log({ name, password, mobile });
  return NextResponse.json({ success: "Data Sent Successfully", ok: true });
}

```
```jsx
/project-root
  /app
    /(auth)
      /login
        page.js
```
```jsx
"use client";
import { useState } from "react";
import React from "react";
import { NextResponse } from "next/server";

const page = () => {
  const [name, setName] = useState("");
  const [password, setPassword] = useState("");
  const [mobile, setMobile] = useState("");

  const handleLogin = async () => {
    const response = await fetch("/api/user", {
      method: "POST",
      headers: {
        "Content-Type": "application/json",
      },
      body: JSON.stringify({ name, password, mobile }),
    });
    const data = await response.json();
    if (data.ok) {
      alert("Login Successful");
    } else {
      alert("Something went wrong");
    }
  };
  return (
    <div className="main flex flex-col justify-center items-center">
      <div>User Login Page</div>
      <div className="login border-4 border-black p-4">
        Name :{" "}
        <input
          className="border-2 border-black mb-4"
          type="text"
          value={name}
          placeholder="Enter your name"
          onChange={(e) => setName(e.target.value)}
        />
        <br />
        Password :{" "}
        <input
          className="border-2 border-black mb-4 "
          type="password"
          value={password}
          placeholder="Enter your password"
          onChange={(e) => setPassword(e.target.value)}
        />
        <br />
        Mobile :{" "}
        <input
          className="border-2 border-black mb-4"
          type="number"
          value={mobile}
          placeholder="Enter your Mobile number"
          onChange={(e) => setMobile(e.target.value)}
        />
        <br />
        <button
          onClick={handleLogin}
          className="mt-4 bg-blue-500 text-white px-4 py-2 rounded"
        >
          Login
        </button>
      </div>
    </div>
  );
};

export default page;
```
