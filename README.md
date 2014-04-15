Heroku Build Pack for PHP and PDO_DBLIB
=======================================

General Information
-------------------

This is yet another buildpack in order to deploy applications
that can connect to Microsoft SQL Server in heroku.

This buildpack is currently composed of:

* FreeTDS 0.9.1
* Apache 2.2.7
* PHP 5.3.28
* libmcrypt 2.5.8 (from heroku-buildpack-php)

pdo_lib has been statically linked to PHP, and you can also
use mongo and/or redis by adding the following lines to php.ini
in your application main directory:

	extension.so
	redis.so

In order to use this buildpack for your heroku application, you
should set the configuration variable BUILDPACK:

	heroku config:set BUILDPACK_URL=https://github.com/erickthered/heroku-buildpack-php

The next time you commit changes to your application, the dyno
should start something like this:

	-----> Fetching custom git buildpack... done
	-----> PHP app detected
	-----> Bundling mcrypt version 2.5.8
	-----> Bundling Apache version 2.2.25
	-----> Bundling FreeTDS version 0.9.1
	-----> Bundling PHP with mongo.so, redis.so and pdo_dblib built-in support
	-----> Discovering process types
	       Procfile declares types -> web

Configuration
-------------

The config files are bundled with the build pack itself:

* conf/httpd.conf
* conf/php.ini
* conf/freetds.conf

