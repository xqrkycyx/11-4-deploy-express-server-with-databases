# Starter: Backend Deployment

This is starter code for the Back End Deployment module. Follow the instructions below to get everything up and running.

This repo was adapted from [this repository](https://github.com/Thinkful-Ed/starter-back-end-deployment) to work with Vercel's most recent updates.

## Server setup instructions

1. Fork and clone this repository.
1. Run `cp .env.sample .env`.
1. Update your `.env` file with a connection URL to your database.
1. Run `npm install`.
1. Run `npx knex migrate:latest`.
1. Run `npx knex seed:run`.

## TL;DR - Module 11, Lesson 4

1. **Create databases:** make 2 new databases on ElephantSQL (`development` and `production`) and copy the two different database URLs
1. **Run migrations on production:** You can run the same migration command as before, but this time with NODE_ENV being equal to the "production" string: `NODE_ENV=production npm run knex -- migrate:latest`
1. **Deploy on Render:** in the _Advanced_ section of the form add an environment variable that contains the key `PRODUCTION_DATABASE_URL` and set the key to `production` database URL from step 1
1. Check `/api/products` on the production server instance to confirm server is deployed, though since the production db wasn't seeded, you'll receive an empty response
1. **Seed production db:** Run `NODE_ENV=production npm run knex -- seed:run` locally to seed the production db
1. Check `/api/products` again on the production server instance; response should return a data payload this time

## Notes / troubleshooting:

- If /api/products returns 502 or some other error, you probably didn't run the migration for the production db
- If the response is successful but empty, make sure you've seeded the production db
- On Render, when setting PRODUCTION_DATABASE_URL environment variable, the value/URL string DOES NOT need to be wrapped in quote (e.g., just directly paste postgres://abcdefgh:\*\*\*@{domain}.db.elephantsql.com/abcdefgh without quotes)

## Live deploy links:

https://simple-server-with-database.onrender.com/

- [/api/products](https://simple-server-with-database.onrender.com/api/products)
- [/api/products/1](https://simple-server-with-database.onrender.com/api/products/1)
- [/api/ping](https://simple-server-with-database.onrender.com/api/ping)
