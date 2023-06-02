# session_cookie_auth_golang

We will build an application with a /signin and a /welcome route.

The /signin route will accept a users username and password, and set a session cookie if successful.
The /welcome route will be a simple HTTP GET route which will show a personalized message to the currently logged in user.

Will define a Refresh HTTP handler to renew the users session token every time they hit the /refresh route in our application

/logout - to invlaidate the session and logs out the user

# Testing
Ensure that http webserver port 8081 is allowed on the firewall

in POSTMAN or http client fire the query..
POST http://10.xxx.xx.97:8081/signin with body 
{
  "username": "user1",
  "password": "user1hasthispassword1"
}

Response : 200 OK and Session Token will be returned
Token ( Session cookie ) can be seen in console output like ...
Session Token is  31602044-525c-41e6-97c2-4da64435b5f5

For Welcome fire the query
GET http://10.xxx.xx.97:8081/welcome
Response : Welcome user1!

For Refresh
POST http://10.xxx.xx.97:8081/refresh
Response: New Session Token is  31602044-525c-41e6-97c2-4da64435b5f5


For logout
GET http://10.xxx.xx.97:8081/logout
Calling the welcome and refresh routes after this will result in a 401 error.