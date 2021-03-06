# Development Guide

### Specifying the port

You can set the environment variable `PORT` to set the port

```shell
PORT=81 npm start
```


### Installing dependencies
This app have npm and Bower dependencies. To install all dependencies in one line, run
```shell
npm i; bower i
```

### Running in development mode
Simply run
```shell
grunt serve
```
if you don't have `grunt` installed, you can run `npm run develop` instead.

You can also specify the port by setting `PORT` environment variable in development mode

```shell
PORT=3000 grunt serve
```

or

```shell
PORT=3000 npm run develop
```

For development it's preferred to have `grunt` installed globally on your machine.  

### Building
To build the project just run:

```shell
grunt build
```
This will build a new version of the web app, ready for production in `/dist` folder

###  Configuration
Swagger Editor will make an XHR GET call to `/config/defaults.json` to get it's settings before launch. If you are using Swagger Editor as a dependency or serving it statically, you can provide your own `defaults.json` at this endpoint to override default settings.

Swagger Editor is configured with a file, [`defaults.json`](../app/config/defaults.json).
Read the [configuration guide](./config.md) and additional details 
in [`defaults.json.guide.js`](../app/config/defaults.json.guide.js)
to learn how to configure Swagger Editor.


### Running with Docker
If you are familiar with [Docker](https://www.docker.com/), a `Dockerfile` is
provided.

Build an image named `swagger-editor`
```shell
sudo docker build -t swagger-editor .
```

Run the container, using the local port 8080 (you may change this to any available
port).
```shell
sudo docker run -ti -p 8080:8080 swagger-editor
```
And open [http://localhost:8080](http://localhost:8080) in your browser

### Code Style
Code style is enforced by [JSCS (JavaScript Code Style)](https://github.com/jscs-dev/node-jscs) and [JSHint](http://jshint.com/). Build will fail if changes in code is not following code style guildlines.

### Testing
To run all tests run

```shell
npm test
```

This will build and run unit tests then if it was successful, it will run  end-to-end tests.

#### Unit tests
All unit tests are located in [`../test/unit`](../test/unit). Unit tests are written in Jasmine and run by Karma. To run unit tests, run

```shell
grunt karma:unit
```

For developing unit tests, run
```shell
grunt test-dev
```
This will keep test browser and test watcher open and watches for file changes to re-run tests.

#### End-to-end tests
All end-to-end tests are located in [`../test/e2e`](../test/e2e). To run end-to-end test, run

```shell
grunt protr
```
This will run [Protractor](http://angular.github.io/protractor/#/) end-to-end test.
