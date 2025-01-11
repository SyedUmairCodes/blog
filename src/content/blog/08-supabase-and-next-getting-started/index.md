---
title: "Supabase and Next.js - Getting Started"
description: "Learning blog series about server-side Next.js and Supabase"
date: "Jan 11 2025"
---

Supabase is a great tool for quickly building robust backends as it provides all the tools and features you need for your backend bundled into a single platform.

I used Supabase for the first time while I was building my final-year graduate project and was amazed how stupidly simple and quick setting up everything was.

I then decided to use it again in a demo project to learn server-side Next.js and the `useOptimistic` hook that React introduced as well as learn how I can add different auth providers in my apps using Supabase as well.

I created a new project in Supabase and used `Bun` for creating a new Next.js application that I will use for implementing all the things I learned. Important to note that I used [this tutorial from Jolly Coding](https://www.youtube.com/watch?v=A6-56miVA_0) as a learning guide but shook things up a little bit around so that they fit my style.

## Creating the project and tables

I created a new project in my Supabase dashboard and named it Listly. I then added a new table by running a SQL query in the project's SQL editor and then enabled row-level security on it and created policies for CRUD operations on tasks table.

## Adding authentication

Supabase provides great documentation about its product and all the things it can do. I set up my server-side authentication using Next's app-router and all I needed to install the `supabase-js` and `ssr` packages that Supabase provides add the project URL and anon key to my environment variables which is avaialble on the same page as the auth setup guide.

According to the documentation we also need a client and server component for our app and its recommended that we store these components in a utils folder for better organization of components.

At this point I didn't knew if I would need more utility components so I stored them in a folder named Supabase inside the utils folder. I forgot that the documentation says that the folder structure should be the same as mine. I just didn't read that. oops.

Supabase is kind enough to provide the started code for both client and server components. I used the code given from Supabase for the server component and it's just an async function that creates a cookie store using the previously mentioned environment variables.

Next, I needed to create a `middleware.ts` file that handles redirecting and checking if the user is authenticated or not using the previously set cookies and since server components can't write cookies, you need middleware to refresh expired auth tokens and store them.

I also needed to create another `middleware.ts` file in the root of my project as well and since I'm using TypeScript I need types for Supabase that I got from my project dashboard.

## Summary

- Created a new Next.js app with bun.
- Created a new project in Supabase.
- Created a table in Supabase, applied RLS and policies on it.
- Added authentication and types in Next.js for Supabase.
- Created middleware for accurate redirecting and navigation.
