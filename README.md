# Debugging JavaScript

This project contains a few examples of debugging in JavaScript (in Node.js and in the browser).


## Requirements

* [git](https://git-scm.com/downloads)
* [NodeJS](https://nodejs.org/en/)


## Get the Code

Download the code for this project by using git clone:
```bash
git clone https://github.com/Learn-by-doing/debugging-javascript.git
```


## Install Node Modules

Like any node project, you will need to run download and install the required node modules for the project to run. Use the following command:
```bash
npm install
```


## Start the App

Once that has finished, you can run the program like this:
```bash
npm start
```

You should see the following if everything is OK:
```
Server started and listening at localhost:3000
```


## Try the Demo

Open your browser to [localhost:3000](http://localhost:3000). You should see a simple search form. Try to search for something like "web" or "javascript". The data being searched is in the [server.js](https://github.com/Learn-by-doing/debugging-javascript/blob/master/server.js#L16) file.

The demo is currently working. Let's switch to the "broken" branch so that we can practice debugging. In your terminal window run the following command:
```bash
git checkout broken
```
This will switch you over to the "broken" branch in your local git repository. The files in the project directory have changed, but only slightly.

Stop the app by pressing `CTRL + C` in your terminal window. Start the app again with `npm start`.

Try the demo again. You will find that it longer works. So let's start debugging.

Open your browser's developer tools (`F12` key in Google Chrome). Inside your developer tools, open the JavaScript console (`ESC` key in Google Chrome). Do you see any errors? You should see something like this:
```
GET http://localhost:3000/search?q=web 500 (Internal Server Error)
```
This means that there was an error on the server. So let's check the server.

Open your terminal window. Do you see any errors there? You should see an error ("stack trace") like this:
```
TypeError: Cannot read property 'toLowerCase' of undefined
    at /home/chill/Projects/current/Learn-by-doing/debugging-javascript/server.js:53:27
    at Array.forEach (native)
    at getMatchingResources (/home/chill/Projects/current/Learn-by-doing/debugging-javascript/server.js:49:12)
    at /home/chill/Projects/current/Learn-by-doing/debugging-javascript/server.js:39:16
    at Layer.handle [as handle_request] (/home/chill/Projects/current/Learn-by-doing/debugging-javascript/node_modules/express/lib/router/layer.js:95:5)
    at next (/home/chill/Projects/current/Learn-by-doing/debugging-javascript/node_modules/express/lib/router/route.js:131:13)
    at Route.dispatch (/home/chill/Projects/current/Learn-by-doing/debugging-javascript/node_modules/express/lib/router/route.js:112:3)
    at Layer.handle [as handle_request] (/home/chill/Projects/current/Learn-by-doing/debugging-javascript/node_modules/express/lib/router/layer.js:95:5)
    at /home/chill/Projects/current/Learn-by-doing/debugging-javascript/node_modules/express/lib/router/index.js:277:22
    at Function.process_params (/home/chill/Projects/current/Learn-by-doing/debugging-javascript/node_modules/express/lib/router/index.js:330:12)
```
This shows a single error that happened in our node app. The first two lines are the most important part:
```
TypeError: Cannot read property 'toLowerCase' of undefined
    at /home/chill/Projects/current/Learn-by-doing/debugging-javascript/server.js:53:27
```
