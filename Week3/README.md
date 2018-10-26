
# Week 2
## Today's Topics
- Putting information in URL parameters
- How to properly structure your web service
- Storing and returning data


### Putting information in URL parameters
So far, we've seen two ways of sending data from the client to the server. The first way was through queries - `/add?num1=5&num2=8` sends the two numbers to the server. The second way was through the body of a request, using JSON. The third way is through something called URL parameters. 

If you look at `params.py`, you'll see a route that looks like `/<word>`. So if you run this file(using `FLASK_APP=params.py flask run`, or the equivalent on windows), and send a GET request to `/somerandomword`, it will print that word out to the screen. If you look in the code, the `<word>` is being extracted into a variable on line 9 that can be used in the method to do any processing. Make sure to play around with this!

There is a second route that does something similar. Send a request to `/users/2` or any other number and see what it prints.  

**Exercise:**
Write a route that listens to POST requests called `/square/<number>` and takes one URL parameter, thats a number. Return the square of that number.


### How to properly structure a web service
So now that we've gone over how to send and receive data, let's start building an actual API. An API stands for Application Programming Interface, and it essentially just means how exactly you'll be communicating with your server (what routes, what parameters, what queries, etc). So let's say we need to design a service to store a bunch of users. A single user is called a **resource**. So when a use wants to register with our service, we create a new user resource and add it to a collection of users that we store in the background. 

Read this article for a really good description of how to design your URLs(https://hackernoon.com/restful-api-designing-guidelines-the-best-practices-60e1d954e7c9). You can ignore the last part about status codes. 

So if you look at `api.py`, I follow the guidelines and have two routes, `/users` and `/users/<username>`. Sending a POST request to `/users` creates a new user based on what the user sends in the body. Sending a GET request to `/users` gets the entire list of users. Now, let's look at the next route. Hypothetically, if you send a GET request to `/users/<username>`, it will get all the information about the user with that specific username(this hasn't been implemented, but that's how it would be if it were). Sending a DELETE request to `/users/<username>` deletes the user with that username. 

Like the article says, you can nest your URLs and make it as complex as necessary. If each user has a list of jobs, you could have routes for `users/<username>/jobs`, and if each job has an id, you could have a route like `/users/<username>/jobs/<jobid>`, etc. 


### Storing data
This part is really simple. Like I mentioned before, I store the user in a list if the client sends a POST request. If they send a GET request, I return the list. 

So essentially, you keep some data structure (a list or a map, if you've taken data structures) to store and retrieve data.

To learn about dictionaries, look at this link. It is pretty essential to be able to store some data for each resource. https://www.w3schools.com/python/python_dictionaries.asp

**Exercise:**
Write an application(a bunch of routes) to do the following:
POST /restaurants - adds a new restaurant to the list of restaurants
GET /restaurants - gets the list of restaurants

DELETE /restaurants/{name} - deletes this restaurant, deleting the list of dishes for it, and deleting the list of ratings for it

POST /restaurants/{name}/dishes - Add new food item to list of food items for restaurant
GET /restaurants/{name}/dishes - get the list of all food items for restaurant

POST /restaurants/{name}/ratings - Add a new rating to list of ratings for restaurant
GET /restaurants/{name}/ratings - Will list ratings of restaurant

Follow the model of how `api.py` stores stuff in a list. For storing the list of dishes for each restaurant, use a dictionary that maps the name of the restaurant to the list of dishes. This part might be tricky, but give it your best!