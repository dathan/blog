---
title: "Rendering With Typescript Nextjs Chakra Ui"
date: 2023-02-15T11:02:09-08:00
draft: true
---


# Motevation

Typically to get me interested in something, if someone needs something from me and says go figure it out, that makes me curious. One such was a particular problem, what and when and how to render in a typescript application. 

My current environment runs on vercel, using Node 18+, nextjs, typescript, strict eslint guidelines, and chakra-ui for the css framework for my custom components.


# Where to Start

For my environment the best place to start is https://nextjs.org/docs/basic-features/pages, there is a section called [two forms of rendering](https://nextjs.org/docs/basic-features/pages#two-forms-of-pre-rendering). Static Generation which is recommended, and from a speed perspective not much else will beat this for a render. So, when is it a good idea to use Server-side Rendering, HTML created on every request?
How do you render each type? What is the pattern that can be communicated to a team to follow for most use cases?


# Most common pattern for Static Rendering I use


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


# But what happens if the page is static (cached) and you want to still show realtime info

We, at PlatoHQ, use a technique that uses the static page to render the inial page with an async realtime fetch and render replace.

Out of the typical cache patterns, Cache Aside, Write-Through, Write-Back, Read-Through, Read-Write, we are using a Read-Through pattern, since we also go back to the source to replace the static file loaded.

## Here is an example

```typescript

export default function PageName({ initalValidRows }) { 
    const { promptLoginOnAuthError } = useContext(AuthPromptContext);
    const { data: session } = useSession();
    const router = useRouter();
    const toast = useToast(); 
    const [rows, setRows] = useState(initialValidRows);
    

    ...

     return(<></>);
 }


```

What is important is what is not communicated. The interface to change data is no longer directly affecting the render, as if you where running the information on the client, but to use hooks to render for the client and for the static file generation properly.

One of the 1st tasks to do is to use an equivelent of the `useEffect()` for our backend for frontend, `trpc.object.method.useQuery(<identifier>, { refetchOnWindowFocus: false  }, onSuccess(rows){ setRows(rows); });`

This will make a graphQL query to our backend, get the rows, and replace the data forcing a re-render onSuccess, this is called Static Generation with Client-side data fetching and can be discussed in detail [here](https://nextjs.org/docs/basic-features/data-fetching/client-side)

We want to do it this way so we can also support SEO/OpenGraph Requests


## What about SSR

In this case we cannot depend on a static version, something needs to be dynamic and loaded from page creation time. There is a case for this. Imagine syncing data from a remote provider then rendering the page. Here is a more concreate example doing such a thing.



