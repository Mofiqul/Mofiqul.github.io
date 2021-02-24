# Implementing Google OAuth2

## Client Application

### Sign up

1. Create OAuth2 client > Pass only client id
2. Generate AuthUrl
3. Retrieve the authorization code [doc](https://googleapis.dev/nodejs/google-auth-library/latest/classes/OAuth2Client.html#getToken)
4. Retrieve the access token, refresh token and id token [doc](https://googleapis.dev/nodejs/google-auth-library/latest/classes/OAuth2Client.html#generateAuthUrl)
5. POST id token to REST server
6. If response is OK (201) then save access token & user details in local storage or cookie, show error message otherwise
7. Use access token as Barer authorization header for request

### Sign in

1. Create OAuth2 client > Pass only client id
2. Generate AuthUrl
3. Retrieve the authorization code [doc](https://googleapis.dev/nodejs/google-auth-library/latest/classes/OAuth2Client.html#getToken)
4. Retrieve the access token, refresh token and id token [doc](https://googleapis.dev/nodejs/google-auth-library/latest/classes/OAuth2Client.html#generateAuthUrl)
5. POST access token to REST server
6. If response is OK (201) then save access token & user details in local storage or cookie, show error message otherwise
7. Use access token as Barer authorization header for request

### Sign out

1. Send token revoke request to REST server
2. On success delete access token and id token from storage

## REST API

### Sign up

1. Get id token from request body
2. Verify the id token and retrieve user profile [doc](https://googleapis.dev/nodejs/google-auth-library/latest/classes/OAuth2Client.html#verifyIdToken)
3. If verified token then create or find user
4. Send user details in response

### Sign in

1. Get the Barer access token for authorization header
2. Verify the access token
3. if verified token then find the user, send unauthorized response otherwise
4. Send user details in response

### Sign out

1. Get the Barer access token from authorization header
2. Revoke the access token [doc](https://googleapis.dev/nodejs/google-auth-library/latest/classes/OAuth2Client.html#revokeToken)
3. On success send not content response
