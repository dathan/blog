---
title: "Mastering High-Performance Inital Loads: A Guide to Using Typescript, Next.js, Chakra UI, and Static Props for Seamless Web Development"
date: 2023-02-15T11:02:09-08:00
draft: false
---


# Motevation

As an Engineer, I'm always on the lookout for new and exciting challenges. So when I was tasked with solving a rendering problem in a Typescript application, I jumped at the opportunity to learn and figure it out.

In this blog post, I'll be sharing my experience and insights into rendering in a Typescript application within a Vercel environment, using Node 18+, Next.js, strict Eslint guidelines, and Chakra UI for custom components. You'll discover how to effectively render content with static props, taking advantage of the benefits of using Typescript and Chakra UI along the way.

Let's dive in and explore the world of rendering with Typescript, Next.js, Chakra UI, and static props.

# Where to Start

For my environment the best place to start is https://nextjs.org/docs/basic-features/pages, there is a section called [two forms of rendering](https://nextjs.org/docs/basic-features/pages#two-forms-of-pre-rendering). Static Generation which is recommended, and from a speed perspective not much else will beat this for an initial bytes to user-render. 

How do you render each type? What is the pattern that can be communicated to a team to follow for most use cases?


# Most common pattern for Static Rendering I use

Jumping into the fastest delivery to the user, a stale page that is configured to stay cached for a minute. Here at build time, we are going to build a static page for every valid row from the database.

```typescript

export const getStaticProps = async () => { // this executes from the build process
  const caller = appRouter.createCaller({ prisma, session: null }); // create a backend interface to the BFF
  const validRows = await caller.schemaObject.getAllValidRows(); // this will not scale when you reach more rows then memory but you get the ideas

  return {
    props: { validRows },
    revalidate: 60, // every minute rebuild
  };
}

```


The above calls the page which is now in the format below, taking validRows as an input.

```typescript

export default function PageName({ validRows }) {
    return(<></>);
}

```

*Note* I am being explicit here with showing that we have a single render.


# But what happens if the page is static (cached) and you want to still show realtime info

We, at PlatoHQ, use a technique that uses the static page to render the inial page with an async realtime fetch and render replace.

Out of the typical cache patterns, Cache Aside, Write-Through, Write-Back, Read-Through, Read-Write, we are using a Read-Through pattern, since we also go back to the source to replace the static file loaded for the inital fast experience.

This came from a need to support Google Search Crawlers, as well as Open Graph Crawlers, so why just make it pages load fast for robots, why not give this experience to the people that matter. Customers.


## Here is an example replace Render

Below is some psuedo code that loads the page from the static built prop and the browser sends a network request to get the rows for display, replacing the `initalValidRows`. This replacement rerenders the page in less then a few 100 ms to a second.

```typescript

export default function PageName({ initalValidRows }) { 
    const { promptLoginOnAuthError } = useContext(AuthPromptContext);
    const { data: session } = useSession({required: true});
    const router = useRouter();
    const toast = useToast(); 
    const [rows, setRows] = useState(initialValidRows);

    trpc.object.method.useQuery(<identifier>, { refetchOnWindowFocus: false  }, onSuccess(rows){ setRows(rows); });`

    ...

     return(<>{rows && console.log(rows)}</>);
 }


```

What is important is what is not communicated. The interface to change data is no longer directly affecting the render, as if you where running the information on the client, but to use hooks to render for the client and for the static file generation properly.

One of the 1st tasks to do is to use an equivelent of the `useEffect()` for our backend for frontend, `trpc.object.method.useQuery(<identifier>, { refetchOnWindowFocus: false  }, onSuccess(rows){ setRows(rows); });`

This will make a graphQL query to our backend, get the rows, and replace the data forcing a re-render onSuccess, this is called Static Generation with Client-side data fetching and can be discussed in detail [here](https://nextjs.org/docs/basic-features/data-fetching/client-side)

We want to do it this way so we can also support SEO/OpenGraph Requests


## What about SSR

In this case we cannot depend on a static version, something needs to be dynamic and loaded from page creation time. This is what SSR promises to offer. I like to think of this as a smarty render from PHP, but it's not as fast. Based on my tests I have found that his is not a feature to render HTML fast, but consistent HTML for non JS browsers. I do not have a use case where NextSEO does not already handle.


## Conclusion

n conclusion, I hope this blog post has been helpful in providing valuable insights and practical guidelines for rendering with Typescript, Next.js, Chakra UI, and static props. After experimenting and testing different methods, I found that using static props significantly reduces the initial load times, from seconds to 100s of milliseconds.

By following the guidelines outlined in this post, you can effectively implement static props in your projects and take advantage of their benefits. Specifically, keep in mind to use static props when more than one user views the page, have only one render return, be aware of hydration errors, and use React hooks to replace stale data immediately.

Overall, rendering is an essential part of web development, and with the right tools and techniques, you can create high-performance and engaging user interfaces. I hope this post has inspired you to take your rendering skills to the next level and explore new possibilities in your projects.
