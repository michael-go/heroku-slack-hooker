# heroku-slack-hooker
A tiny nodejs server that translates [Heroku](http://heroku.com) deploy-hooks to [Slack](http://slack.com)'s webhooks 

## Why?
Slack already has a Heroku integration builtin, but missing a small basic feature: showing the log of commits made between current and previous deploys

## Usage
1. deploy `heroku-slack-hooker` to a server:
  1. we deal with heroku... so lets deploy this to heroku too: 
  ```sh
  heroku create <myhooker>
  git push heroku master
  ```
  suppose the url is: `https://<myhooker>.herokuapp.com`
2. go to Slack settings => Integrations 
  1. add a new 'Incoming Webhook', select a channel
  2. copy the `Webhook URL` value. (we'll refer it as: `<slack-webhook-url>`)
3. `cd` into a heroku project you want to connect with Slack and run:

  ```sh
     heroku addons:add deployhooks:http https://<myhooker>.herokuapp.com/hook/<slack-webhook-url>
  ```
  (this can be also done in Heorku's dashboard webui)

It should work now :)
  
  
