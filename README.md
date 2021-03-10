## This is a starter template for [Learn Next.js](https://nextjs.org/learn).

### The two forms of pre-rendering: Static Generation and Server-side Rendering.

- Static Generation is the pre-rendering method that generates the HTML at build time. The pre-rendered HTML is then reused on each request.
- Server-side Rendering is the pre-rendering method that generates the HTML on each request.

###

By default, Next.js pre-renders every page. This means that Next.js generates HTML for each page in advance, instead of having it all done by client-side JavaScript. Pre-rendering can result in better performance and SEO.

Each generated HTML is associated with minimal JavaScript code necessary for that page. When a page is loaded by the browser, its JavaScript code runs and makes the page fully interactive. (This process is called hydration.)

### getStaticProps - Only for static generation

- Essentially, getStaticProps allows you to tell Next.js: “Hey, this page has some data dependencies — so when you pre-render this page at build time, make sure to resolve them first!
- You can also query the database directly. This is possible because getStaticProps only runs on the server-side. It will never run on the client-side.

### To use Server-side Rendering, you need to export getServerSideProps instead of getStaticProps from your page

### getServerSideProps

- Because getServerSideProps is called at request time, its parameter (context) contains request specific parameters.

You should use getServerSideProps only if you need to pre-render a page whose data must be fetched at request time. Time to first byte (TTFB) will be slower than getStaticProps because the server must compute the result on every request, and the result cannot be cached by a CDN without extra configuration.

### getStaticPaths - https://nextjs.org/learn/basics/dynamic-routes/page-path-external-data

## Steps to generate dynamic routes

- First, we’ll create a page called [id].js under pages/posts. Pages that begin with [ and end with ] are dynamic routes in Next.js.

In pages/posts/[id].js, we’ll write code that will render a post page — just like other pages we’ve created.

- Now, here’s what’s new: We’ll export an async function called getStaticPaths from this page. In this function, we need to return a list of possible values for id.
- In development (npm run dev or yarn dev), getStaticPaths runs on every request.
  In production, getStaticPaths runs at build time.
- Dynamic routes can be extended to catch all paths by adding three dots (...) inside the brackets. For example:
  pages/posts/[...id].js matches /posts/a, but also /posts/a/b, /posts/a/b/c and so on.
- getStaticProps and getStaticPaths runs only on the server-side. It will never be run on the client-side. It won’t even be included in the JS bundle for the browser. That means you can write code such as direct database queries without them being sent to browsers.

# todo https://nextjs.org/learn/basics/deploying-nextjs-app

### API - http://localhost:3000/api/hello
