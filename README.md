# Tutorial Spotify API
<img src="https://upload.wikimedia.org/wikipedia/commons/3/33/Spotify_logo13.png" width="180"> 

Spotify Web API provides easy access to a huge library of songs and theirs audio features. At this tutorial, we will learn how to retrieve data from multiple Spotify API endpoints and how to play with it using pandas.

## An Introduction to using APIs
Application Program Interfaces, or APIs, are commonly used to retrieve data from remote websites. Sites like Reddit, Twitter, and Facebook all offer certain data through their APIs. To use an API, you make a request to a remote web server, and retrieve the data you need.

## API Requests
APIs are hosted on web servers. When you type www.google.com in your browser’s address bar, your computer is actually asking the www.google.com server for a webpage, which it then returns to your browser.

APIs work much the same way, except instead of your web browser asking for a webpage, your program asks for data. This data is usually returned in JSON format.

In order to get the data, we make a request to a webserver. The server then replies with our data. In Python, we’ll use the requests library to do this.

## Type of requests
There are many different types of requests. The most commonly used one, a GET request, is used to retrieve data.

We can use a simple GET request to retrieve information from the OpenNotify API.

response  = requests.get(url='https://api.spotify.com/v1/search', params= {'q':playlist, 'type':'playlist'})
response = req.json()
```ruby
require 'redcarpet'
markdown = Redcarpet.new("Hello World!")
puts markdown.to_html
```

OpenNotify has several API endpoints. An endpoint is a server route that is used to retrieve different data from the API. For example, the /comments endpoint on the Reddit API might retrieve information about comments, whereas the /users endpoint might retrieve data about users. To access them, you would add the endpoint to the base url of the API.

The first endpoint we’ll look at on OpenNotify is the iss-now.json endpoint. This endpoint gets the current latitude and longitude of the International Space Station. As you can see, retrieving this data isn’t a great fit for a dataset, because it involves some calculation on the server, and changes quickly.

You can see a listing of all the endpoints on OpenNotify here.

The base url for the OpenNotify API is http://api.open-notify.org, so we’ll add this to the beginning of all of our endpoints.

## Status codes
The request we just made had a status code of 200. Status codes are returned with every request that is made to a web server. Status codes indicate information about what happened with a request. Here are some codes that are relevant to GET requests:

200 – everything went okay, and the result has been returned (if any)
301 – the server is redirecting you to a different endpoint. This can happen when a company switches domain names, or an endpoint name is changed.
401 – the server thinks you’re not authenticated. This happens when you don’t send the right credentials to access an API (we’ll talk about authentication in a later post).
400 – the server thinks you made a bad request. This can happen when you don’t send along the right data, among other things.
403 – the resource you’re trying to access is forbidden – you don’t have the right permissions to see it.
404 – the resource you tried to access wasn’t found on the server.
We’ll now make a GET request to http://api.open-notify.org/iss-pass, an endpoint that doesn’t exist, per the API documentation.

response = requests.get("http://api.open-notify.org/iss-pass")
print(response.status_code)

## Hitting the right endpoint
iss-pass wasn’t a valid endpoint, so we got a 404 status code in response. We forgot to add .json at the end, as the API documentation states.

We’ll now make a GET request to http://api.open-notify.org/iss-pass.json.

response = requests.get("http://api.open-notify.org/iss-pass.json")
print(response.status_code)

## Query parameters
You’ll see that in the last example, we got a 400 status code, which indicates a bad request. If you look at the documentation for the OpenNotify API, we see that the ISS Pass endpoint requires two parameters.
