1. What is responsible for defining the routes of the games resource?

line 17 of server,js is:    const gamesRouter = createRouter(gamesCollection);
This uses the createRouter function from the create_router.js file in the helper folder. The final parts of the routes are set in this function (e.g. '/' or '/:id'). The actual id of the stored game comes from the database.

line 18 of server.js is:    app.use('/api/games', gamesRouter);
This sets the middle segment of the route (i.e. /api/games ).

line 20 of server.js is:    app.listen(9000, function(){
This sets the port of the route.

so a full route of http://localhost:9000/api/games/ is set in server.js with the imported createRouter function from create_router.js.

2. What do you notice about the folder structure? What's the client responsible for? What's the server responsible for?

The client has folders for components, containers and services. From this file naming/structure I think the client is responsible for displaying information and retrieving and requesting edits to the records.

The server has folders for db and helpers. The first is for setting up database information and the second concerns handling the client's requests and then making relevant changes to the database or retrieving records.

3. What are the the responsibilities of server.js?

server.js creates the games router and specifies the port the server is running on. It also connects to the MongoDB database.

4. What are the responsibilities of the gamesRouter?

The gamesRouter specifies the endpoints for the routes and what to do with the information from the HTML request such as saving a new record from a JSON payload into the database and also what to send back to the client as the HTML response.

5. What process does the the client (front-end) use to communicate with the server?

the client uses a fetch request with a method (GET, POST or DELETE), this is sent to a specific path/URL and if required also has a body (with JSON) and a header.

6. What optional second argument does the fetch method take? And what is it used for in this application? Hint: See Using Fetch on the MDN docs

The optional arguments are the method, body and headers in this app. The method is used to specify if it is a DELETE or a POST request and the body and headers are used in the POST request to tell the server what to save to the DB.

7. Which of the games API routes does the front-end application consume (i.e. make requests to)?

'http://localhost:9000/api/games/' for POST and GET

and

'http://localhost:9000/api/games/(id)' for DELETE

where id is the id of the game record to be deleted

8. What are we using the MongoDB Driver for?

This must allow the server to communicate with the database. So we can access and edit the database.