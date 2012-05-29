ThinkUp OpenShift Quickstart
=========================
ThinkUp is a free, open source web application that captures all your activity on social networks like Twitter, Facebook and Google+. With ThinkUp, you can store your social activity in a database that you control, making it easy to search, sort, analyze, publish and display activity from your network. All you need is a web server that can run a PHP application.

You can see ThinkUp in action at http://www.thinkupapp.com

Getting (Quickly) Started with ThinkUp on OpenShift
--------------------

Sign up for an openshift account at http://openshift.redhat.com/

Install the OpenShift Client tools on your machine if you don't have them. You can find more info here: https://openshift.redhat.com/app/getting_started

Create an OpenShift PHP application:

	rhc-create-app -a thinkup -t php-5.3 -l $your_login

ThinkUp requires a MySQL db. Add mysql support to your application:
    
	rhc-ctl-app -a thinkup -e add-mysql-5.1 -l $your_login

Make a note of the username, password, and host name you are given. You'll need these to complete the configuration of ThinkUp once you deploy.

Add this upstream ThinkUp quickstart repo:

	cd thinkup/php
	rm -rf *
	git remote add upstream -m master git://github.com/jaboutboul/ThinkUp-OpenShift-Quickstart.git
	git pull -s recursive -X theirs upstream master

Then push the repo upstream to OpenShift

	git push

Voila. You are now up and running. Log into the you app:

	http://thinkup-$your_login.rhcloud.com

Run through the ThinkUp install/configuration.
