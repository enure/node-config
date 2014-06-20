Configure your Node.js Applications
===================================

**Version 1.0** ([release notes](https://github.com/lorenwest/node-config/wiki/Upgrading-From-Config-0.x)): Node-config is ready to break out of its pre-1.0 shell since the original release in Oct. 2010.  Version 1.0 preview is in the current master branch, and will be published to npm after a short soaking period. Check out the master branch if you'd like a preview prior to the npm release.

[![NPM](https://nodei.co/npm/config.svg?downloads=true&stars=true)](https://nodei.co/npm/config/)&nbsp;&nbsp;
[![Build Status](https://secure.travis-ci.org/lorenwest/node-config.svg?branch=master)](https://travis-ci.org/lorenwest/node-config)&nbsp;&nbsp;
[release notes](https://github.com/lorenwest/node-config/master/History.md)

Introduction
------------

Node-config organizes configurations for your app deployments.

Define a set of default parameters,
and extend them for different deployment environments (development, qa,
staging, production, etc.).

It provides a consistent interface for accessing configurations in your app modules, and within a [growing list of sub-modules](https://www.npmjs.org/browse/depended/config) using config.

Project Guidelines
------------------

* *Simple* - Get started fast
* *Powerful* - For multi-node enterprise deployment
* *Flexible* - Supporting multiple config file formats
* *Lightweight* - Small file and memory footprint
* *Predictable* - Well tested foundation for module and app developers

Quick Start
---------------
The following examples are in JSON format, but configurations can be in other [file formats](https://github.com/lorenwest/node-config/wiki/File-Formats-&-Comments).


**Install in your app directory, and edit the default config file.**

    $ npm install config
    $ mkdir config
    $ vi config/default.json

    {
      // Cusomter module configs
      "Customer": {
        "dbConfig": {
          "host": "localhost",
          "port": 5984,
          "dbName": "customers"
        },
        "credit": {
          "initialLimit": 100,
          // Set low for development
          "initialDays": 1
        }
      }
    }

**Edit config overrides for production deployment:**

    $ vi config/production.json

    {
      "Customer": {
        "dbConfig": {
          "host": "prod-db-server"
        },
        "credit": {
          "initialDays": 30
        }
      }
    }

**Use configs in your code:**

    var config = require('config');
    ...
    var dbConfig = config.get('Customer.dbConfig');
    db.connect(dbConfig, ...);

**Start your app server:**

    $ export NODE_ENV=production
    $ node my-app.js

Running in this configuration, the `port` and `dbName` elements of `dbConfig`
will come from the `default.json` file, and the `host` element will
come from the `production.json` override file.

Articles
--------

* [Configuration Files](https://github.com/lorenwest/node-config/wiki/Configuration-Files)
* [Common Usage](https://github.com/lorenwest/node-config/wiki/Common-Usage)
* [Environment Variables](https://github.com/lorenwest/node-config/wiki/Environment-Variables)
* [Reserved Words](https://github.com/lorenwest/node-config/wiki/Reserved-Words)
* [Command Line Overrides](https://github.com/lorenwest/node-config/wiki/Command-Line-Overrides)
* [Multiple Node Instances](https://github.com/lorenwest/node-config/wiki/Multiple-Node-Instances)
* [Sub-Module Configuration](https://github.com/lorenwest/node-config/wiki/Sub-Module-Configuration)
* [Configuring from a DB / External Source](https://github.com/lorenwest/node-config/wiki/Configuring-from-a-DB-/-External-Source)
* [External Configuration Management Tools](https://github.com/lorenwest/node-config/wiki/External-Configuration-Management-Tools)
* [Examining Configuration Sources](https://github.com/lorenwest/node-config/wiki/Examining-Configuration-Sources)
* [Using Config Utilities](https://github.com/lorenwest/node-config/wiki/Using-Config-Utilities)
* [Upgrading from Config 0.x](https://github.com/lorenwest/node-config/wiki/Upgrading-From-Config-0.x)

Contributors
------------
<table id="contributors" noborder><tr><td noborder><img src=https://avatars.githubusercontent.com/u/373538?><a href="https://github.com/lorenwest">lorenwest</a></td><td noborder><img src=https://avatars.githubusercontent.com/u/791137?><a href="https://github.com/josx">josx</a></td><td noborder><img src=https://avatars.githubusercontent.com/u/133277?><a href="https://github.com/enyo">enyo</a></td><td noborder><img src=https://avatars.githubusercontent.com/u/1656140?><a href="https://github.com/eheikes">eheikes</a></td><td noborder><img src=https://avatars.githubusercontent.com/u/842998?><a href="https://github.com/nsabovic">nsabovic</a></td></tr><tr><td noborder><img src=https://avatars.githubusercontent.com/u/506460?><a href="https://github.com/Osterjour">Osterjour</a></td><td noborder><img src=https://avatars.githubusercontent.com/u/145742?><a href="https://github.com/jberrisch">jberrisch</a></td><td noborder><img src=https://avatars.githubusercontent.com/u/1918551?><a href="https://github.com/nitzan-shaked">nitzan-shaked</a></td><td noborder><img src=https://avatars.githubusercontent.com/u/3058150?><a href="https://github.com/Alaneor">Alaneor</a></td><td noborder><img src=https://avatars.githubusercontent.com/u/125062?><a href="https://github.com/keis">keis</a></td></tr><tr><td noborder><img src=https://avatars.githubusercontent.com/u/157303?><a href="https://github.com/cmcculloh">cmcculloh</a></td><td noborder><img src=https://avatars.githubusercontent.com/u/16861?><a href="https://github.com/abh">abh</a></td><td noborder><img src=https://avatars.githubusercontent.com/u/28898?><a href="https://github.com/DMajrekar">DMajrekar</a></td><td noborder><img src=https://avatars.githubusercontent.com/u/2533984?><a href="https://github.com/jonjonsonjr">jonjonsonjr</a></td><td noborder><img src=https://avatars.githubusercontent.com/u/157474?><a href="https://github.com/k-j-kleist">k-j-kleist</a></td></tr><tr><td noborder><img src=https://avatars.githubusercontent.com/u/12112?><a href="https://github.com/GUI">GUI</a></td><td noborder><img src=https://avatars.githubusercontent.com/u/811927?><a href="https://github.com/bolgovr">bolgovr</a></td><td noborder><img src=https://avatars.githubusercontent.com/u/672821?><a href="https://github.com/Askelkana">Askelkana</a></td><td noborder><img src=https://avatars.githubusercontent.com/u/941125?><a href="https://github.com/hisayan">hisayan</a></td><td noborder><img src=https://avatars.githubusercontent.com/u/937179?><a href="https://github.com/Esya">Esya</a></td></tr><tr><td noborder><img src=https://avatars.githubusercontent.com/u/865153?><a href="https://github.com/eiriksm">eiriksm</a></td><td noborder><img src=https://avatars.githubusercontent.com/u/1087986?><a href="https://github.com/jscharlach">jscharlach</a></td><td noborder><img src=https://avatars.githubusercontent.com/u/3645924?><a href="https://github.com/mmoczulski">mmoczulski</a></td></tr></table>

License
-------

May be freely distributed under the [MIT license](https://raw.githubusercontent.com/lorenwest/node-config/master/LICENSE).

Copyright (c) 2010-2014 Loren West
[and other contributors](https://github.com/lorenwest/node-config/graphs/contributors)

