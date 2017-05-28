Application Program Interfaces, or APIs, are commonly used to retrieve data from remote websites. Sites like Reddit, Twitter, and Facebook all offer certain data through their APIs. To use an API, you make a request to a remote web server, and retrieve the data you need.

## API Requests
APIs are hosted on web servers. When you type www.google.com in your browser’s address bar, your computer is actually asking the www.google.com server for a webpage, which it then returns to your browser.

APIs work much the same way, except instead of your web browser asking for a webpage, your program asks for data. This data is usually returned in JSON format (for more on this, checkout our tutorial on working with JSON data).

In order to get the data, we make a request to a webserver. The server then replies with our data. In Python, we’ll use the requests library to do this. 

## Type of requests
There are many different types of requests. The most commonly used one, a GET request, is used to retrieve data.
We can use a simple GET request to retrieve information from the Spotify API.

Spotify has several API endpoints. An endpoint is a server route that is used to retrieve different data from the API. 
To access them, you would add the endpoint to the base url of the API.

The first endpoint we’ll look at on Spotify is the */search* endpoint. This endpoint gets some information about the item requested.

You can see a listing of all the endpoints on Spotify [here](https://developer.spotify.com/web-api/endpoint-reference/).

### Endpoints
GET https://api.spotify.com/v1/search


```python
import requests
response = requests.get(url='https://api.spotify.com/v1/search', params= {'q':'Radiohead', 'type':'playlist'})
response_json = response.json()
```

### Request Parameters
(q) The search query's keywords (and optional field filters and operators), for example q='Radiohead'. 

(type) A comma-separated list of item types to search across. Valid types are: album, artist, playlist, and track.
### Response Format
On success, the HTTP status code in the response header is 200 OK and the response body contains an array of artist objects, simplified album objects and/or track objects (wrapped in a paging object) in JSON format. On error, the header status code is an error code and the response body contains an error object.
