# homework14

Homework 14. 

File functionally. 

1.	To launch the app, user invokes server.js from the terminal CLI. This action does the following: 
a.	Initializes express server session 
b.	Initializes passport for credential management 
c.	Tells the app to use API and HTML routes from respective files
d.	Then it uses index.js from /models folder to setup the tables (if force = true) and/or to update the tables using the model found in user.js file. 
e.	Sets up a listener on 8080 port
2.	When a visitor connects to localhost/8080, the app responds by serving up the signup page. If the user is unauthenticated login.html is served. If the user is authenticated, then the app redirects to the ‘/members’ html route that will serve members.html page. 
3.	The login page is served up. The styles contained in ‘/style.css’ and bootstrap css are applied. Login.js script is also connected to the html. This script will handle user events. In particular it:
a.	Collects input from the form 
b.	Validates that there is an input 
c.	Posts the values to the “users” table via the api route file using the sequelize model
d.	Once there is a success - js will redirect to the ‘/members’ route. This route corresponds to server serving up the members.html file. 
i.	One note – the user model hashes the password. This means that the literal password will be encrypted such that validation happens not on the decrypted value but on the encrypted value. Another point is that it is impossible to “decrypt” the pwd such that the original pwd is revealed. 
4.	Signup.html offers a visitor an opportunity to signup by entering an email and a password. Signup.js will handle the user actions. The event that is relevant is user pressing the “Sign Up” button.  Simply it will:
a.	Collect the data from the form 
b.	Use an ajax post request to invoke the “api/signup” route. 
c.	The route will invoke sequelize to make a post to the database by passing table name, user name and the password 
d.	Sequelize will use the model contained in model.js file and post the entry fields 
i.	It will hash the password before posting by using the bccrypt library
5.	Members.html just shows logged in user’s data. There is an API route that looks up the member ID based on the information entered in the previous step (login or signup).
6.	Package.json lists out all the dependencies in the project. This makes for an easy code sharing without having to move the node_modiles every time. Code recipient can simply “npm install” the modules and run the app.
7.	Package-lock.json list out all of the versions of the modules used by the app. This stipulates the library version woth which the app works. If there is a subsequent update to a library the app will still download the older version. It is up to the developer to update the libraries and test whether the app works with the new library version. 
 


