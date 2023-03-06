# Notetaker - an example of a T3 app with Daisy UI

## What is Notetaker?
Notetaker allows the user to keep notes organized by topics.
Users must sign in using their GitHub account to create and view notes.
Notes can be written in Markdown, so they are displayed in a formatted way.

You can find a deployed app [here](https://notetaker-yurivyatkin.vercel.app/).

## What technologies does this app use?

The initial app's configuration and design follow along with Jack Herrington's YouTube video [T3: TRPC, Prisma and NextAuth Done Right](https://www.youtube.com/watch?v=J1gzN1SAhyM).

### T3 Stack

This is a [T3 Stack](https://create.t3.gg/) project bootstrapped with `create-t3-app`.

We try to keep this project as simple as possible, so you can start with just the scaffolding we set up for you, and add additional things later when they become necessary.

If you are not familiar with the different technologies used in this project, please refer to the respective docs. If you still are in the wind, please join our [Github](https://t3.gg/github) and ask for help.

- [Next.js](https://nextjs.org)
- [NextAuth.js](https://next-auth.js.org)
- [Prisma](https://prisma.io)
- [Tailwind CSS](https://tailwindcss.com)
- [tRPC](https://trpc.io)

To learn more about the [T3 Stack](https://create.t3.gg/), take a look at the following resources:

- [Documentation](https://create.t3.gg/)
- [Learn the T3 Stack](https://create.t3.gg/en/faq#what-learning-resources-are-currently-available) — Check out these awesome tutorials

You can check out the [create-t3-app GitHub repository](https://github.com/t3-oss/create-t3-app) — your feedback and contributions are welcome!

### Better Tailwind CSS with daisyUI

[Tailwind CSS](https://tailwindcss.com/) is great for styling UI elements without writing CSS stylesheets.
However, for the common types of UI, the direct use of utility classes becomes repetitive and tedious.

[daisyUI](https://daisyui.com/) adds classes to Tailwind CSS for all common UI components. Classes like `btn`, `card`, etc. This allows us to focus on important things instead of making basic elements for every project.

The customizing and theming abilities of daisyUI allow the implementation of any design system.

### PostgreSQL database made easy

This project assumes using a PostgreSQL database.

One of the easiest ways to obtain an instance of the PostgreSQL database is to sign up at [Supabase](https://supabase.com).

Alternatively, one can run Supabase [locally using Docker](https://www.linode.com/docs/guides/installing-supabase/):

Clone the repository:
```sh
git clone --depth 1 https://github.com/supabase/supabase
```

Enter the directory with the `docker-compose.yml` file:
```sh
cd supabase/docker
```

Make and edit a copy of the included configuration file:
```sh
cp .env.example .env
```

Run Supabase:
```sh
docker-compose up
```

Of course, there are more conventional ways to run PostgreSQL.
Any method will do.

One of the advantages of Supabase is its web console, but it also provides other useful features, including authentication, cloud storage, and auto-generated APIs.

## How to run this project?

Clone the repository to your local machine:
```sh
git clone git@github.com:yurivyatkin/notetaker.git
```

Install the dependencies:
```sh
npm install
```

Configure the environment variables in the `.env` file:
```env
# Prisma
DATABASE_URL="postgresql://<your PostgresQL database connection string>"

# Next Auth
NEXTAUTH_URL="http://localhost:3000"

# Next Auth Github Provider
GITHUB_CLIENT_ID=""
GITHUB_CLIENT_SECRET=""
```

Push the table definitions to the newly configured database:
```sh
npx prisma db push
```

## How do I deploy this?

Generate a [secret](https://next-auth.js.org/configuration/options#secret) for NextAuth, using this command:
```
openssl rand -base64 32
```

Use this secret as the value of the `NEXTAUTH_SECRET` environment variable.

For production deployments, the `NEXTAUTH_URL` environment variable is not used.

GitHub requires configuring a separate app for use in the production, so there will be different values of the `GITHUB_CLIENT_ID` and `GITHUB_CLIENT_SECRET` environment variables.

To push the tables to the remote instance of PostgreSQL, create a `.env.production.local` file with the `DATABASE_URL` environment variable set to the corresponding PostgreSQL connection string. Then use the following command:
```sh
npm run push:production
```

Follow the deployment guides for [Vercel](https://create.t3.gg/en/deployment/vercel), [Netlify](https://create.t3.gg/en/deployment/netlify), and [Docker](https://create.t3.gg/en/deployment/docker) for more information.
