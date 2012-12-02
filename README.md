## Setup on Heroku

### Create app

```bash
$ heroku create
$ git push heroku master
```

### Setup Trello config vars

Get your application keys here: https://trello.com/1/appKey/generate

```bash
$ heroku config:add TRELLO_API_KEY=...
$ heroku config:add TRELLO_OAUTH_SECRET=...
```

Get your user access token by substituting your api key into the following url

```
https://trello.com/1/authorize?key=YOUR_API_KEY_GOES_HERE&name=Zendesk+Importer&expiration=never&response_type=token&scope=read,write
```

```bash
$ heroku config:add TRELLO_ACCESS_TOKEN_KEY=...
```

The board id can be found in the url when viewing a board

```bash
$ heroku config:add TRELLO_BOARD_ID=...
```

This is the name of the list in Trello in which new tickets will be created

```bash
$ heroku config:add TRELLO_LIST=Support Tickets
```

This is optional. If you would like new Trello tickets created by the importer to be assigned a label, set this config var with the label color.

```bash
$ heroku config:add TRELLO_LABEL=blue
```

### Setup Zendesk config vars

```bash
$ heroku config:add ZENDESK_URL=https://mycompany.zendesk.com
$ heroku config:add ZENDESK_USERNAME=your@email.addr
```
In Zendesk, Settings -> Channels -> API -> Token Access

```bash
$ heroku config:add ZENDESK_TOKEN=...
```

Integer id of Zendesk view

```bash
$ heroku config:add ZENDESK_VIEW=...
```

### Setup the scheduler addon

https://devcenter.heroku.com/articles/scheduler

use the following command:

```
bundle exec bin/import-tickets
```
