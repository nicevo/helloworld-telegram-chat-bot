# Telegram bot

## Preparation

You will need this:

* Application for editing Python code, such as [PyCharm](https://www.jetbrains.com/pycharm/) (the community edition is both free and capable)
* Heroku account. Sign up for free on [www.heroku.com](https://signup.heroku.com/dc).
* Telegram account. Sign up for free on [telegram.org](https://telegram.org/).
* The Heroku CLI (a tool for deploying applications to Heroku)
* The Heroku Builds plugin for the Heroku CLI

### Install Heroku CLI

First, [install the Heroku CLI](https://devcenter.heroku.com/articles/getting-started-with-python#set-up) (we use this to manage our Heroku applications)

Second, install the Heroku Builds plugin for the Heroku CLI (we use this to upload our applications to Heroku):
  ```
  heroku plugins:install heroku-builds
  ```

## Step By Step

### Tell Telegram you want to create a bot

Sign in to Telegram and do this:
- Start chatting with the bot BotFather by sending him the message ```/newbot```.
- Answer BotFather's questions.
- After a couple of questions you will get a message starting with "Done! Congratulations...". This message will contain your API key (i.e. the password for your bot).
- Save the API key in a text file on your computer, for later use.

### Hello World Sample Bot

[Download and extract code to a new folder](https://github.com/nicevo/helloworld-klarna/archive/step-telegram.zip).

### Create the app in Heroku

Open a terminal window and go to the folder when you extracted the source code.

Run this commands:
```
heroku apps:create
heroku ps:scale web=1 --app NAME_OF_YOUR_HEROKU_APPLICATION
```

You will now see something like this:

    Creating app... done, ⬢ powerful-everglades-32132
    https://powerful-everglades-32132.herokuapp.com/ | https://git.heroku.com/powerful-everglades-32132.git
    
The name of the app in this example was _powerful-everglades-32132_.

Open `init_webhook.py` and make sure the URL of your application name is in the `set_webhook` call. It should look 
something like this, using our example above:

    https://powerful-everglades-32132.herokuapp.com

Make your API key, sent to you by BotFather, available to your Heroku application by entering this command in your terminal:

```
heroku config:set TELEGRAM_BOT_APIKEY=your-bot-api-key --app NAME_OF_YOUR_HEROKU_APPLICATION
```
- Re-deploy to Heroku using the same command as before:
```
heroku builds:create --app NAME_OF_YOUR_HEROKU_APPLICATION
```

- Start chatting with your bot. You should now be able to find your bot in Telegram by searching for it using the name you sent to BotFather earlier. 
- Verify that it sends back everything you send to it.

You now have a fully functional bot!

## Next steps

In `app/views.py` there is a function called `process_text`. Use that to change the text and make the bot smarter.

If you want something to get you started you can try these [ideas on chat bots](./bots-ideas.md).

## A Closer Look

Want to know more about Telegram bots? Check out <https://core.telegram.org/bots>.

We're using Flask, a web service library for Python, and a lot of information about it can be found on <https://blog.miguelgrinberg.com/post/the-flask-mega-tutorial-part-i-hello-world>.

More reading about Heroku:

- Heroku Architecture: <https://devcenter.heroku.com/categories/heroku-architecture>
- Python on Heroku: <https://devcenter.heroku.com/articles/getting-started-with-python>
- Heroku CLI cheat sheet: <http://ricostacruz.com/cheatsheets/heroku.html>
- Heroku CLI usage: <https://devcenter.heroku.com/articles/using-the-cli>
