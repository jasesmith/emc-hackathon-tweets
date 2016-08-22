EMC Hackathon Tweets!
-----

## Tag: badass-step-05

This step adds code to pull tweets into the UI **as raw JSON data** using angular $http

1. index.html - Displays authenticated status true | false
2. app.js - When the controller loads (when the page loads), it calls /auth, which does authentication with twitter to get a key, then responds with JSON containing  `{auth : true}`
3. server.js - Adds the /auth endpoint, which will call the twitter auth API to get a key.  If you're feeling brave, read more about twitter [twitter oauth here](https://dev.twitter.com/oauth/application-only)
4. This step includes the /tweets API which uses the [twitter search API](https://dev.twitter.com/rest/public/search) to search twitter for specific keywords and return a list of tweets
5. In **app.js** we're using the main controller to first call `/auth` then call `/tweets` and stick the data on $scope so it can be displayed in index.html

6. **NEXT** : Now start building a real UI.  Put those tweets in some type of list using angular `ng-repeat`


Ensure all the packages in package.json are installed by running `npm install`

Start your server with
`node server.js`

Then point your browser to `http://localhost:5000`

The server APIs look like this:

```
GET /tweets

{
    "search_metadata": {
        "completed_in": 0.007,
        "count": 50,
        "max_id": 726174093180018700,
        "max_id_str": "726174093180018688",
        "next_results": "?max_id=726146153826373631&q=from%3Aguychurchward%20OR%20%40emc%20OR%20%23emc&count=50&include_entities=1",
        "query": "from%3Aguychurchward+OR+%40emc+OR+%23emc",
        "refresh_url": "?since_id=726174093180018688&q=from%3Aguychurchward%20OR%20%40emc%20OR%20%23emc&include_entities=1",
        "since_id": 0,
        "since_id_str": "0"
    },
    "statuses": [
        {
            "contributors": null,
            "coordinates": null,
            "created_at": "Fri Apr 29 22:19:30 +0000 2016",
            "entities": {
                "hashtags": [
                    {
                        "indices": [
                            61,

 ...
```

```
POST /auth

response
{
    "auth": true,
    "data": {
        "access_token": "AAAAAAAAAAAAAAAAAAAAAA9LtwAAAAAAeihb7UwP%2B6hq8GZBlS0HKH%2Bu1qs%3DWAzj5p8Aq67HPskRnFi6ydvN0nogHIyH8Vg4znGo2dDiruNncC",
        "token_type": "bearer"
    }
}
```

```
GET /foo
curl http://localhost:5000/foo
{"hello":"world"}
```


```
PUT /bar
curl --request PUT --data '{"a": 1}' http://localhost:5000/bar
{"status":"OK"}
```

### The rest is up to you.  Get busy!
