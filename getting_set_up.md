Getting Set Up
===============

In these steps you'll download Typo, get it running on your local system, verify that its test suite passes, and do a test deployment to Heroku.  You'll also setup an account on Pivotal Tracker, which you'll use to setup tasks for part 2.
 
1) Install Typo locally (see "[Typo + GitHub Setup Instructions](#typo--github-setup-instructions)" below)  
2) Get the Typo test suite and make sure all specs pass green. Pending specs are fine. Run the following commands:
```
$ bundle exec rake cucumber
$ bundle exec rake spec
```
3) Setup a free [Pivotal Tracker](https://www.pivotaltracker.com) account, create a public project for this assignment, and add your pair partners as collaborators (obviously only one of you needs to do this).  
4) Make sure Typo can be deployed to Heroku (see "[deploying to heroku](#deploying-to-heroku-instructions)" instructions below).
 

Typo + GitHub Setup Instructions
--------------------------------

1. Fork the Typo repository: https://github.com/saasbook/typo  (Typo is open source, but we have snapshotted the repo including fixing some failing tests and using a stable revision for Ruby 1.9.3 - note that so far in the course we have been on Ruby 2.2.2 - if you don't have Ruby 1.9.3 install it via `rvm install 1.9.3`)
2. Now clone your forked Typo repository into a folder on your local machine.
3. Run `sudo apt-get update`
4. Run `sudo apt-get install libxml2-dev libxslt-dev`
5. Run `sudo chmod o+t -R /tmp`
6. Run bundle install --without production in the Typo directory. 
7. Run the database migration in the Typo directory (`rake db:migrate`).
 

Deploying to Heroku Instructions
--------------------------------

Typo wasn’t built with Heroku in mind, but the changes needed to deploy to Heroku have already been made in our fork of the Typo repository. If you haven't done it previously you will need to run the following at the command line:

```
$ heroku login
$ ssh-keygen
$ heroku keys:add
```

Then from within your copy of the Typo repository, run:
 
```
$ heroku create
$ git push heroku master
$ heroku run rake db:migrate
$ heroku open # doesn't work on C9 --> on C9 right click on link that git push to heroku generates
```

At this point a browser should open and take you to typo setup. Follow the onscreen instructions but **please make a careful note of the password it generates for you**.  Once you leave the page with the password on you can't reset it unless you want to work out how to get typo set up to send email on Heroku.  Note that you'll need this password for your homework submission.

Next: [Fixing a Bug in Typo](fixing_a_bug_in_typo.md)
