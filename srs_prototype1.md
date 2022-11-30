# Maderia
## Prototype 1
In the context of this document, the word "user" means a person who wants to see hotels and book rooms, "hotel" is just a hotel that has (or wants to have) an account in our system, and "client" is a general term used to refer to both users and hotels.

In addition to that, "username" means a unique identifier that a client chooses upon registration. 

In the context of this document, the word "function" is used to imply any process in general. It is not limited to the programming construct we normally call "function".

### User requirement specifications

1. The system should allow new clients to be registered.
2. The system should register clients in two categories: "Users" and "Hotels".
3. The system should allow registered clients to log in and log out.
4. The system should allow registered clients to delete their accounts.

### System requirement specifications
### General
1. The website will have 3 pages: the login page (one page for both users and hotels), a register page (one page for both users and hotels) and an index page.

#### The login functionality
1. The login page should be able to "switch" between the user-login mode and hotel-login mode. By switching, it is meant that the UI of the page changes, asking potentially different information when in the two modes. Also, the login page should send the login data to different end-points of the database depending on whether it's a user or a hotel that's logging in.
2. In user-login mode, the login page should ask for a username or email (written in the same input field) and a password of length >=6. In hotel-login mode, the loin page asks the same information as in the user-login mode (for this 1st prototype) but it will send the input data to a different endpoint of the back-end.
2. When a client requests the main (index) page of the website, the website should identify if the client is logged in or not and respond with the user login page (if the client is not logged in) or the main (index) page if the client is logged in. More about the index page later ...
3. Once a client is logged in, the website should remember the login session and not ask the client to log in again unless the client logs out. (even if the the browser tab is closed and re-opened).
4. while a client tries to log in, the website should be able to reject passwords that are less than 6 characters only with front-end logic (without sending the data to the back-end). As described in the "Register functionality" section, The website only accept password length >= 6 while registration. So if a client tries to log in with a password length < 6, The page should display an error message saying that the password can't be correct.
5. Clients should be able to use both their username or email (along with their password) to log into the website. Clients should enter their username or email into the same input field on the login page and the back-end code should know whether to use the data as a username or email based on the existance of the '@' symbol in the string.
6. The login page should be able to display a relevant error message when the username / email is not found among the registered users in the database or when the username / email is found but the password is incorrect. Displaying an error message in this case happens after sending the login data to the back-end and getting a response.
7. If the username / email and password sent from the login page to the back-end is all correct, The back end code should log the user in, send the index page as a response, and from that moment on, remember that the user is logged in on that browser until the user logs out. (i.e. if we close the browser or the browser tab and re open it and navigate to the website, it should know that we're logged in and respond with the index page, not the login page.)

#### The register functionality
1. The register page should be able to "switch" between user-register mode and hotel-register mode. In user-register mode, the page should ask for the full name of the user, a unique email of the user, a unique usernmame of the user. (neither the email nor the username should be registered before.), and a password that is at least 6 characters long. In hotel-login mode, instead of asking for a full name, the register page should ask for the name of the hotel (this should be unique too.)
2. The register page should send the registration data 
3. There should be a password confirmation input field on the register page. We make sure the password and password confirmation fields have similar value (with client-side logic) before sending the data for the server to examine and register.
4. The register page should show relevant error messages when the password is less than 6 characters long, when the given username, email, or hotel name is already registered with some other account.
5. If the registration data sent from the register page to the back-end is all correct and valid, the back-end code registers the client, logs them in, and redirects them to the index page.
6. Users and hotels are different entities in the database. So they should be stored in their own separate tables upon registration.
7. For this prototype, (1st version) the database schema for the user and hotel entities depends on what data we collect while registering those two entities. (i.e. full name, username, email, password in user table and hotel name, username, email, password in hotels table).

#### The index page
1. The index page is a page that only logged in clients are supposed to see. The login functionality, upon successful login, should redirect to the index page and that should be the only way the index page can be accessed.
2. The index page should be mapped to (associated with) the root url of the website (which is "/").
3. An attempt to go to the index page directly (like entering the index page url in the browser) should trigger a back-end function that first checks if the client is logged in and redirects to the login page if the client is not logged. if the client is already logged in, such a function should dimply respond with the index page.
4. The index page, for this first prototype, should mostly be a blank page with the text "This is the index page. You are logged in as a [hotel/user] with username: [username]", with the elements in the angle brackets replaced with the real type (hotel/user) of the client and the real username of the client that's logged in. The index page should not be formatted with any front-end css code.
5. For the index page to contain information about the currently logged in client, the back-end code should pass (inject) that information into the index page. (maybe by using template tags or placeholders).
6. The index page should also contain a "logout" button that, when clicked, triggers the logout functionality in the back-end code. and a "delete account" button that triggers the account deletion function in the back-end code.

#### The logout functionality
1. the logout function at the back-end should be triggered by the "logout" button on the index page.
2. Once a client logs out, the back-end should identify any subsequent requests coming from that browser as not logged in. Thus, for example, requests for the index page will be redirected to the login page.

#### The delete account functionality
1. When clients press the "delete account" button on the home page, they should be presented with a warning message and asked to confirm their choice (with front-end logic).
2. If clients confirm their choice to delete their account, the index page should send the username of the client to a back-end function that first triggers the logut functionality and then removes the entry with the received username from the database tables.






