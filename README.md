FORMAT: 1A
HOST: https://virtserver.swaggerhub.com/ElafrisInc/DashboardAPI/1.0.0

# Client Dashboard Backend-Frontend API


# Group users

## Users Login [/users/login]

### Login for users [POST]
By passing in login and password, you can search for

such user credentials in the system and get a token for the session. To logout - frontend just forgets the token and by default all users without a token are redirected to login screen

+ Request (application/json)
    + Attributes (Users Login Request)


+ Response 200 (application/json)

        login successful

    + Attributes (Users Login Response)


+ Response 401 

        Authentication failed




+ Response 422 

        Validation failed





## Users Recover [/users/recover]

### Recover password for users [POST]
Email is sent and checked in the DB. If there is such email in DB - then the letter is sent with a link, which can be used to reset the password

+ Request (application/json)
    + Attributes (Users Recover Request)


+ Response 200 



+ Response 404 

        User not found





## Users [/users/]

### Visible user profiles [GET]
Return a list of user profiles which user can view and edit. Backend checks and returns the list according to user's role.

+ Response 200 



### Create and invite new user [POST]
Creates a new user with specific role and permissions

+ Response 200 



+ Response 403 

        Insufficient role permissions




+ Response 404 

        User not found





## Users By Username [/users/{username}]

+ Parameters
    + username (string, required)


### Edit user role and permissions [PUT]
Write new user role and permissions

+ Response 200 



+ Response 403 

        Insufficient role permissions




+ Response 404 

        User not found




### Delete user [DELETE]
Deletes user from DB

+ Response 200 



+ Response 403 

        Insufficient role permissions




+ Response 404 

        User not found





## Users By Domain [/users/{domain}]

+ Parameters
    + domain (string, required)


### User list for domain [GET]
Return list of the user profiles which user can view and edit. Backend checks and returns the list according to user's role and chatbot domain to filter for.

+ Response 200 



+ Response 403 

        Insufficient role permissions




+ Response 404 

        Chatbot domain not found






# Group profile

## Users Profile By Username [/users/profile/{username}]

+ Parameters
    + username (string, required)


### Populate user profile details [GET]
Return list of the user profile details to populate the profile form. Backend checks and returns the profile according to user's role and checks if username is available to read and write.

+ Response 200 



+ Response 403 

        Insufficient role permissions




+ Response 404 

        User not found




### Edit user profile details [PUT]
Write new user profile details

+ Response 200 



+ Response 403 

        Insufficient role permissions




+ Response 404 

        User not found






# Group dialogs

## Dialogs [/dialogs/]

### Dialogs list view for all domains [GET]
Return the list of dialogs for all domains

+ Response 200 




## Dialogs By Domain [/dialogs/{domain}]

+ Parameters
    + domain (string, required)


### Dialogs list view for domain [GET]
Return the list of dialogs for a specific chatbot domain

+ Response 200 



+ Response 404 

        Domain not found





## Dialogs detailed view [/dialogs/detailed/{dialog}]

+ Parameters
    + dialog (string, required)


### Dialogs detailed view [GET]
Return the detailed view of a dialog by dialog id

+ Response 200 



+ Response 404 

        Dialog not found






# Group domains

## Domains [/domains]

### Chatbot domains  list [GET]
Return the domain list for both /dialogs and /users for filtering. Also methods reserved for future to CRUD /domains.

+ Response 200 




## Settings for Domain [/domains/{domain}]

+ Parameters
    + domain (string, required)


### Domain settings [GET]
Return settings for the specific chatbot domain

+ Response 200 



+ Response 403 

        Insufficient role permissions




+ Response 404 

        Chatbot domain not found




### Domain settings adjust [PUT]
Adjust the settings for the specific chatbot domain

+ Response 200 



+ Response 403 

        Insufficient role permissions




+ Response 404 

        Chatbot domain not found






# Group reports

## Reports Usage By Domain [/reports/usage/{domain}]

+ Parameters
    + domain (string, required)


### Domain usage report [GET]
Return the usage report for the specific domain

+ Response 200 



+ Response 404 

        Chatbot domain not found





## Reports Liveagent By Domain [/reports/liveagent/{domain}]

+ Parameters
    + domain (string, required)


### Domain live agent requests report [GET]
Return the live agent requests report for the specific domain

+ Response 200 



+ Response 404 

        Chatbot domain not found





## Reports Unrecognized By Domain [/reports/unrecognized/{domain}]

+ Parameters
    + domain (string, required)


### Domain unrecognized intents report [GET]
Return the unrecognized intents report for the specific domain

+ Response 200 



+ Response 404 

        Chatbot domain not found






# Data Structures

## Users Login Request (object)


### Properties
+ `email`: `user@company.com` (string, required) 
+ `password`: `QwErTy@` (string, required) 


## Users Login Response (object)


### Properties
+ `token`: `eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6InN1cGVyQGVsYWZyaXMuY29tIiwiX2lkIjoiNTlmOWRmZTM3Yzc2ZjkyZGE5NGM5YWUwIiwiaWF0IjoxNTExODgzNTI2fQ.qeDtT7vtdnkNWufTc_-sCD6_U4t772i5tJmQj0xpJIg` (string, optional) 
+ `user`: `eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6InN1cGVyQGVsYWZyaXMuY29tIiwiX2lkIjoiNTlmOWRmZTM3Yzc2ZjkyZGE5NGM5YWUwIiwiaWF0IjoxNTExODgzNTI2fQ.qeDtT7vtdnkNWufTc_-sCD6_U4t772i5tJmQj0xpJIg` (User, optional) 


## User (object)


### Properties
+ `id` (string, required) 
+ `email`: `user@company.com` (string, required) 
+ `name`: `Widget Adapter` (string, required) 


## Users Recover Request (object)


### Properties
+ `email`: `user@company.com` (string, required) 
