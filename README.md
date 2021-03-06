# Twitch Tracker Backend

This is the backend server of the Twitch tracker project, powered by [Node.js](https://nodejs.org), [Express](https://expressjs.com).
The corresponding [FrontEnd](https://github.com/ThomasProust/twitch-frontend.git) of the application needs to this to be able to run.

## Prerequisites

You need to have [Node.js](https://nodejs.org) and [npm](https://nodejs.org) installed on your machine.
This project requires a connection to a [mongo](https://mongodb.com) database in order to work properly.
In order to use the automatic reload of the server for development, you will need to have `nodemon` installed in your machine.

```
npm install -g nodemon
```

## Setup

Install dependencies by running `npm install`

Before running the application, create a `.env` file at the root directory of the project with the following variables:

```
MONGO_URI="<_url_to_your_mongo_db>"
TWITCH_CLIENT_ID="<_a_twitch_client_id>"
TWITCH_SECRET="<_a_twitch_secret>"
TWITCH_OAUTH_TOKEN="<o_auth_token_for_the_application"
```

The twitch credentials can be obtain from your account on [Twitch](https://dev.twitch.tv/console).

## Start server

In order to start the server, just enter `npm start` from your cli.
You should then be able to make requests to the following url
`http://localhost:5000`

To run the server with automatic reload, you can enter `npm run dev` from your cli. _Nodemon required_

In order for your [FrontEnd](https://github.com/ThomasProust/twitch-frontend.git) to run smoothly, you should create the corresponding resources:

Via curl:

```sh
curl -X POST http://localhost:5000/games -H "Content-Type: application/json" -d '{"name": "Far Cry 5"}'
curl -X POST http://localhost:5000/games -H "Content-Type: application/json" -d '{"name": "Assassin\s creed odyssey"}'
curl -X POST http://localhost:5000/games -H "Content-Type: application/json" -d '{"name": "Tom Clancy's Rainbow Six Siege"}'
```

or via the API doc.

## API doc

The API documentation for this project is generated by [swagger](https://swagger.io/).
Once your backend is running, you can visualize the specifications through the following path:

if you running the project locally: http://localhost:5000/doc

otherwise you can check it directly from the live [application](https://secure-eyrie-57390.herokuapp.com/doc/)

## Testing

In order to run the test, you will need to have a connection to a mongo database. The tests will run the operations involving mongo in a separate database named as follow : `YOUR-DATABASE-NAME_test`.

Run `npm run test` to execute the tests via [Jest](http://jestjs.io).
