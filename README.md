# Pipefy API Documentation

This is the Pipefy API documentation, here you will find a guide through all the resources you can actually get on it.

## Disclaimer

Pipefy is in beta version and this API documentation could be deprecated at any time. When it got officialy released you will be notificated, and then we will be awared of our API users.


## Current Version

We don't actually have a versioned API, because we are on a beta version and our API could break at any time. If you cannot handle with unexpected API changes, we discourage the use of it.

## Schema

All API access is over HTTPS, on the <tt>app.pipefy.com</tt>. All data is sent and received as JSON.

All timestamps are returned on ISO 8601 format:

> YYYY-MM-DDTHH:MM:SSZ

## Authentication

All the requests to Pipefy's resources must be authenticated, otherwise you'll get a `401 Unauthorized` HTTP status response.

The only way you can authenticate requests to Pipefy API is through the user API key and email. You can do it by two ways:

### Sent in header:

```bash
curl -H "X-User-Email: youremail@example.com" -H "X-User-Token: 1ap0h4n1u1hb0198-ah01" https://app.pipefy.com/users/current.json
```

### Sent in parameters:

```bash
curl https://app.pipefy.com/users/current.json?user_email=youremail@example.com&user_token=1ap0h4n1u1hb0198-ah01
```

### Examples of usage

Some API endpoints are documented with an example of its usage. All examples
are javascript + Jquery source code, testable on your browser's javascript
console if you are logged in on pipefy.
