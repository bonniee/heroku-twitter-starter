# heroku-twitter-starter

Using Heroku's scheduler, post tweets at a regular interval.

This repo is forked from [heroku_ebooks by @tommeagher](https://github.com/tommeagher/heroku_ebooks). I wanted a stripped-down, bare-bones example of how to use the Twitter API with Heroku.

## Setup

1. Clone this repo
2. Create a Twitter account that you will post to.
3. Sign into https://dev.twitter.com/apps with the same login and create an application. Make sure that your application has read and write permissions to make POST requests.
4. Make a copy of the `local_settings_example.py` file and name it `local_settings.py`
5. Take the consumer key (and secret) and access token (and secret) from your Twiter application and paste them into the appropriate spots in `local_settings.py`.
6. Create an account at Heroku, if you don't already have one. [Install the Heroku toolbelt](https://devcenter.heroku.com/articles/quickstart#step-2-install-the-heroku-toolbelt) and set your Heroku login on the command line.
7. Type the command `heroku create` to generate the Python app.
8. The only Python requirement for this script is [python-twitter](https://github.com/bear/python-twitter), the `pip install` of which is handled by Heroku automatically.
9. `git commit -am 'updated the local_settings.py'`
10. `git push heroku master`
11. Test your upload by typing `heroku run worker`. Check your Twitter account to see if it worked.
12. Now it's time to configure the scheduler. `heroku addons:create scheduler:standard` (You'll need to add a credit card to your account if you haven't already - but don't worry, we'll be using the Free tier.)
13. Once that runs, type `heroku addons:open scheduler`. This will open up a browser window where you can adjust the time interval for the script to run. The scheduled command should be `python bot.py`. I recommend setting it at one hour.
14. Sit back and enjoy the fruits of your labor.
