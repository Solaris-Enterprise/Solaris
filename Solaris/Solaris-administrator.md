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
