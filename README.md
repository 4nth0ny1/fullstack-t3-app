Authenticated T3 Todo App

Steps

- [x] npm create t3-app@latest

Backend

- [x] Update Prisma Schema

  1. add Todo model to the prisma schema
  2. add the model to the database
     a. npx prisma db push
     b. npx prisma studio and look at the database

- [x] Add Email auth provider

  1. add EmailProvider to the /server/auth.ts file and replace DiscordProvider
  2. install nodemailer for EmailProvider
     a. npm install nodemailer
     b. https://next-auth.js.org/providers/email
  3. added EMAIL_SERVER, EMAIL_FROM, AND EMAIL_API_KEY to .env file

- [x] Create tRPC router for Todos
  1. created /server/api/routers/todo.ts
     a. removed publicProtected code and created a get all todos route
  2. created /src/types.ts
  3. import /src/types.ts into /api/routers/todos.ts
     a. insert into input()
  4. proceed to create all, create, delete, toggle api routes
  5. change /server/api/root.ts from exampleRouter to todoRouter

FrontEnd

- [x] Login

  1. update the /src/pages/index.tsx page
  2. restart the server
  3. try to login with test email
  4. use the link in the terminal to view protected route
  5. npx prisma studio > to check if the user recorded were saved in the db

- [x] List Todos

  1. create Todos and Todo component
  2. update types.ts file for Todos type
  3. import the Todos type to Todo component
  4. Add markup to the Todo Component

- [x] Create Todos

  1. create createTodos.tsx component
  2. install react-hot-toast
  3. add Toaster to \_app.tsx file
  4. add toast validation to the createTodos.tsx
  5. add the newTodo mutation
  6. should get a 200 from the network tab on creation
  7. check the studio it should have todo data
  8. added useContext to add todo to the list on frontend

- [x] Toggle Todo

  1. added doneMutation to the todo
  2. checked the network tab and the prisma studio and it persists

- [x] Delete Todo

  1. copy and paste the doneMutation and change it to deleteMutation.
  2. checked network tab and prisma studio and it worked.

- [x] Optimistic updates
      def: when you don't wait to get something back from the server. we can optimistically update the frontend ahead of the server request from cached results. it will delete instantly for better user experience.
  1. added optimistic update to CreateTodo function
  2. tested it by slowing the throttle in dev tools to slow3g to see the placeholder before the data persists
  3. added the ability to test user experience with TRPC error on /server/api/router/todo.ts and changed the 'placeholder' to newTodo. if you uncomment the TRPC error it will not allow the user to post and the toast will appear. when commented everythign works as expected.
  4. add optimistic delete on Todo.tsx component
  5. add optimistic update on doneMutation in Todo.tsx component
  6. tested with slow3g and it was very fast which indicates that we are getting optimistic updates and deletes
  7. adding onSuccess to Todo.tsx, don't test this on slow3g because it doesn't have the optimistic updates. it will be super slow.

---

# Create T3 App

This is a [T3 Stack](https://create.t3.gg/) project bootstrapped with `create-t3-app`.

## What's next? How do I make an app with this?

We try to keep this project as simple as possible, so you can start with just the scaffolding we set up for you, and add additional things later when they become necessary.

If you are not familiar with the different technologies used in this project, please refer to the respective docs. If you still are in the wind, please join our [Discord](https://t3.gg/discord) and ask for help.

- [Next.js](https://nextjs.org)
- [NextAuth.js](https://next-auth.js.org)
- [Prisma](https://prisma.io)
- [Tailwind CSS](https://tailwindcss.com)
- [tRPC](https://trpc.io)

## Learn More

To learn more about the [T3 Stack](https://create.t3.gg/), take a look at the following resources:

- [Documentation](https://create.t3.gg/)
- [Learn the T3 Stack](https://create.t3.gg/en/faq#what-learning-resources-are-currently-available) — Check out these awesome tutorials

You can check out the [create-t3-app GitHub repository](https://github.com/t3-oss/create-t3-app) — your feedback and contributions are welcome!

## How do I deploy this?

Follow our deployment guides for [Vercel](https://create.t3.gg/en/deployment/vercel), [Netlify](https://create.t3.gg/en/deployment/netlify) and [Docker](https://create.t3.gg/en/deployment/docker) for more information.
