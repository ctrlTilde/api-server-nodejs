# [Nodejs API Server](https://github.com/ctrlTilde/api-server-nodejs)

Express / NodeJS Starter with JWT authentication and **SQLite** persistence - Provided by `Ctrl Tilde`.
Authentication flow uses `json web tokens` via passport library - `passport-jwt` strategy.

> Tested with:

| NodeJS     | NPM | YARN | 
|------------| --- | --- | 
| `v16.19.0` | ✅ | ✅ | 


## ✨ Requirements

- [Node.js](https://nodejs.org/) >= v16.10
- [SQLite](https://www.sqlite.org/index.html)

## ✨ How to use the code

> 👉 **Step 1** - Clone the project
```bash
$ git clone https://github.com/ctrlTilde/api-server-nodejs.git
$ cd api-server-nodejs
```

> 👉 **Step 2** - Install dependencies via `Yarn`
```bash
$ yarn
```

> 👉 **Step 3** - Run the SQLite migration via TypeORM
```bash
$ yarn typeorm migration:run
```

> 👉 **Step 4** - Edit the `.env` using the template `.env.sample`. 
```env
PORT=5050                       # API PORT
SQLITE_PATH=./database.db       # Path to the SQLite database file
SECRET="Whatever-STRONG"        # Secret for sensitive data hashing 
```

> 👉 **Step 5** - Start the API server (development mode)
```bash
$ yarn dev
```

```bash
< ROOT / src >
     | 
     |-- config/                              
     |    |-- config.ts             # Configuration       
     |    |-- passport.ts           # Define Passport Strategy             
     | 
     |-- migration/
     |    |-- some_migration.ts     # database migrations
     |
     |-- models/                              
     |    |-- activeSession.ts      # Sessions Model (Typeorm)              
     |    |-- user.ts               # User Model (Typeorm) 
     | 
     |-- routes/                              
     |    |-- users.ts              # Define Users API Routes
     | 
     | 
     |-- index.js                   # API Entry Point
     |-- .env                       # Specify the ENV variables
     |                        
     |-- ************************************************************************
```

## ✨ SQLite Path

The SQLite Path is set in `.env`, as `SQLITE_PATH`


## ✨ API

For a fast set-up, use this POSTMAN file: [api_sample](https://github.com/ctrltilde/api-server-nodejs-pro/blob/main/media/api.postman_collection.json)

> 👉 **Register** - `api/users/register`

```
POST api/users/register
Content-Type: application/json

{
    "username":"test",
    "password":"pass", 
    "email":"test@example.com"
}
```

---
> 👉 **Login** - `api/users/login`

```
POST /api/users/login
Content-Type: application/json

{
    "password":"pass", 
    "email":"test@example.com"
}
```
---

> 👉 **Logout** - `api/users/logout`

```
POST api/users/logout
Content-Type: application/json
authorization: JWT_TOKEN (returned by Login request)

{
    "token":"JWT_TOKEN"
}
```
---


## ✨ Update role for existing user

> 👉 Using yarn:

```$ yarn update-role [user_id] [role_id (optional)]```

- [user_id] is the id of existing user to update role for.
- [role_id] is the id of role: 1 for admin & 2 for user. If you don't provide any role_id it would update user to admin role.

## ✨ Run the Tests (`minimal suite`)

```
$ yarn test
```
