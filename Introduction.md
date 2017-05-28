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

## Example: Search for an Item 
Get Spotify catalog information about artists, albums, tracks or playlists that match a keyword string.
> Endpoint:  https://api.spotify.com/v1/search

### Request Parameters
*/search* endpoint requires two parameters:
> **q** : The search query's keywords (and optional field filters and operators), for example q='Radiohead'. 

> **type**: A comma-separated list of item types to search across. Valid types are: album, artist, playlist, and track.
We can make a dictionary with these parameters, and then pass them into the requests.get function.
```python
params= {'q':'Radiohead', 
         'type':'artist'}
```
Let's make our first API request and print the status code:
```python
import requests
response = requests.get(url='https://api.spotify.com/v1/search', params= {'q':'Radiohead', 'type':'artist'})
response.status_code
```
The request we just made had a status code of 200. That means thata everything went okey and the result has been returned. 

```python
response_json = response.json()
```
### JSON
JSON is the primary format in which data is passed back and forth to APIs, and most API servers will send their responses in JSON format.

Python has great JSON support, with the json package. The json package is part of the standard library, so we don’t have to install anything to use it. We can both convert lists and dictionaries to JSON, and convert strings to lists and dictionaries.
```python
import json
response_json = response.json()
```
