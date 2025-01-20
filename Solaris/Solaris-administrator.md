# Administrator

## Server Features

- REST API.
- SSE (EventSource).

## Permissions & Credentials

- One super administrator (is also setup during deployment of control server).
  - The super admin has access to managing other admins.
    - Adding & Removing admins
    - Changing credentials for admins.

- Super administrators has 3 layers of security.
  - Password.
  - 2FA.
  - 12 word secret (which is given).

- Administrators must always have 2 layers of security.
  - Password.
  - 2FA.
  
## First Super Admin

After the control server has been deployed the IT professional uses the default credentials to login to the admin dashboard to reroll the secret words and change the username, password and additonally sets his 2fa up.

By default the server will be put in a hold state until the IT professional sets up a secure and valid super admin account.

## Enpoints & Schema

- Authentication.
- Inventory (of yaml recipes).
  - CRUD operations.
- Execute recipes.
  - Direct execution (ie sending recipie directly with request).
  - Server execution (ie providing ID of recipies wanted to be executed on chosen agents).
  
### Authentication

---
`/auth/login`

###### Request

```json
{
  "username": "",
  "password": "",
  "secret_words": [], // May be omitted since it's only a super admin feature.
  "2fa": ""
}
```

###### Response

```json
{
  "token": "",
  "expiry_date": 0,
}
```

---
`/auth/reroll_2fa`

(Unsure of the behavior of this endpoint at the moment.)

### Admin Management

These groups of endpoints will only be authorized to be used by the super admin.

**This endpoint is exclusive to super admins.**

**These endpoints are using SBA.**

---
`/super/reroll_secrets`

###### Response

```json
{
  "secret_words": []
}
```

#### (I will continue the schema in future. It's basically CRULD operations)

### Inventory

`/`

###### Request

```json
{
  "username": "",
  "password": "",
  "2fa": ""
}
```

###### Response

```json
{
  "token": "",
  "expiry_date": 0,
}
```

### Execution of Recipes

---
`/exec`

###### Request

```json
{
  "targets": [], // Id's for each targeted agent
  "recipies": [] // Id's for each task recipe
}
```

---
`/exec/direct`

###### Request

```json
{
  "targets": [], // Id's for each targeted agent
  "recipe": "" // The yaml reciple inlined for execution
}
```

###### Response

`200 OK`