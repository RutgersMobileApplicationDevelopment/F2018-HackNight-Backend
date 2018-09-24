
# Week 2
## Today's Topics
- Using Postman to send requests
- Different kinds of HTTP methods
- Putting data in the body


### Postman
1) https://www.getpostman.com/. Open it up. 
2) Run the `methods.py` flask app we have given, like we did last week.
3) Go to Postman. In the URL field, put in 127.0.0.1:5000/hello.
4) To the left of the URL, make sure it says "GET", otherwise click on the dropdown and select "GET". 
5) Press send. 
6) You should see a messaging saying "You have sent a GET request."
7) Now, change the "GET" to a "POST" and press send. You should see "You have sent a POST request."

This is the general idea of different kinds of HTTP methods. You can have one route, `/hello`, and have it do different things based on what kind of request you send it. See the next section for more details.


### Different kinds of HTTP methods
When you put a URL in the browser, your browser implicitly sends a GET request. This is what we did last week. When you typed in "127.0.0.1:5000/one" in your browser, it sent a GET request to that URL. A GET request is used when you're trying to retrieve, or "get", data from a server. There are several types of requests you can use using the HTTP protocol, and GET is simply one of them. Now, look at the file we have provided, `methods.py`.

Last wee, we wrote our code in `HelloWorld.py` like this:
```
@app.route("/")
def hello():
    return "Hello Flask"
```

But now, in `methods.py`, we have:
```
@app.route("/hello", methods=['GET', 'POST'])
def hello():
    return "Hello Flask"
```

This means we're listening for both GET requests and POST requests on our route `/hello`. Last week, we were only listening for GET requests, implicitly. 

Read this (https://www.tutorialspoint.com/http/http_methods.htm) description of some common HTTP methods(GET, POST, PUT, DELETE) and their use cases, and try to do your own research on how this works. As usual, ask us if you have any questions,but try to figure it out yourself first!

**Exercise:**
1) Write a new route that listens for POST requests only, call it `/add`. Have it take two numbers as user input(remember from last week!) and return the sum of the two numbers. 
2) Modify the `/add` route to also listen for GET requests. Have it return a random number when called. You'll have to look up how get random numbers in Python. 

Note - you should never separate this kind of functionality(exercise 2) based on the method that was used. This is only for your understanding and practice!

### Sending complex data
Up till
