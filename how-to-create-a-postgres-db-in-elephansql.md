# How to create a PostgreSQL Database in ElephantSQL.com

To get started with our database is important to note that we will not run or install Postgres ourselves, we will use the [elephansql.com](elephantsql.com) online service to setup and run an empty database we can then configure further to store our app's information.

## Creating a Database

To create an instance of a Postgres Database in ElephantSQL.com follow these steps:

1. Create an account or Sign in with GitHub or Google (recommended) by going to https://customer.elephantsql.com/login
2. Once logged in click the **Create new instance** button ![create new instance button](./assets/create-instance-btn.png)
3. Fill out the form by giving your database a **name** like `my_app_db` and selecting **Plan**: Tiny Turtle (Free). You can leave the tags field empty
4. **Select a region and data center**: Pick any region from the list preferably in the US. Then click the review button ![review button](./assets/review-btn.png)
5. **Confirm new instance**: Review your database information and click Create Instance ![create instance confirm btn](./assets/create-instance-confirm.png)

<details>
<summary> See a Gif of these steps here</summary>

![creating a database in ElephantSQL.com](./assets/elephantsql-creating-db.gif)
</details>

## Using the Database

Once in your ElephantSQL dashboard which displays your database instances **locate** and **click** in the database you just created. In your Database details page find and copy the URL for the database. Your URL would look something like: `postgres://ialnuwjg:RWewY6BlQ0idpnTY4JHAJHBzhwf1hfoz@kashin.db.elephantsql.com:5432/ialnuwjg`

We will use this URL to access and modify the database. This is the URL that your back-end server will use to connect to the database.

To create tables and setup your database, we recommend you use Beekeeper Studio, which is a cross-platform Postgres Client and SQL editor.

1. Download and install Beekeeper Studio from https://www.beekeeperstudio.io/get
2. Open Beekeeper Studio and connect to your database using the database URL by:
   1. Copying the database url
   2. Clicking the **Import from URL** button and pasting the database URL in the popup dialog box and clicking **Import**
   3. Lastly, click the **Connect** button.
  
  See the Gif below for these steps:
![beekeeper studio connecting to elephansql](./assets/connecting-to-elephansql.gif)
3. Once you are connected then you will be able to inspect your database and execute any SQL code in it. For an example see the screenshot below:

![running sql code in beekeeper studio](./assets/running-code-in-beekeeperstudio.png)

## Connecting to your Database in your Back-end Server

To connect to your database from your server running on Repl.it, save your Database URL as Secret Environment Variable with the name `DATABASE_URL` as seen in the gif below.

![Adding an environment variable to a replit app](./assets/replit-env-variables.gif)

>To learn more read [Staying safe: Keeping your passwords and other secrets secure - Repl.it](https://docs.replit.com/tutorials/08-storing-secrets-and-history_)

Your database url will be available in `process.env.DATABASE_URL`. For example to connect to your database using `pg-promise` you would write the following code.

```js
const pgp = require('pg-promise')();
const DATABASE_URL = process.env.DATABASE_URL

const db = pgp(DATABASE_URL)
```
