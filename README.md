# Jenkins ci skip plugin

[![Build Status](https://travis-ci.org/banyan/jenkins-ci-skip-plugin.png)](https://travis-ci.org/banyan/jenkins-ci-skip-plugin)
[![Coverage Status](https://coveralls.io/repos/banyan/jenkins-ci-skip-plugin/badge.png)](https://coveralls.io/r/banyan/jenkins-ci-skip-plugin)
[![Bitdeli Badge](https://d2weczhvl823v0.cloudfront.net/banyan/jenkins-ci-skip-plugin/trend.png)](https://bitdeli.com/free "Bitdeli Badge")

Skip making a build for certain push. Just add `[ci skip]` into your commit's message to let Jenkins know, that you do not want to perform build for the next push.

By default this plugin also skips builds for commits with [maven-release-plugin] anywhere in message.

Full example:

```
$ git commit -m 'documentation update [ci skip]'
$ git commit -m '[maven-release-plugin] prepare for next development iteration'
```

It is very useful when you are working things unrelated to application's code such as README. This feature idea comes from [Travis CI](http://about.travis-ci.org/docs/user/how-to-skip-a-build/).

## Installation

Install the plugin from the Jenkins Plugin Manager.

### Enabling ci-skip

In the job configuration, check Enable ci-skip.

![A Screenshot](docs/enable.png)

### How it works

Jenkins is based on works by changeset, so if there is changeset from before build and commit includes `[ci skip]`, then build is skipped with 'SUCCESS' status.
If there is no changeset, it will be build.

## Development:

Install RVM and jruby:
http://rvm.io/rvm/install

rvm install jruby

```
$ sudo apt-get uninstall ruby1.8 ruby
$ sudo apt-get install ruby1.9.1 ruby1.9.1-dev # this is actually Ruby 1.9.2
$ sudo ln -s /usr/bin/ruby1.9.1 /usr/bin/ruby
# Now download RubyGems from https://rubygems.org/pages/download
$ tar xvzf rubygems-1.x.x.tgz
$ cd rubygems-1.x.x
$ sudo ruby setup.rb
$ sudo ln -s /usr/bin/gem1.9.1 /usr/bin/gem
$ sudo gem install bundler
$ sudo gem install jpi
$ bundle install
$ ./bin/start-jenkins
$ open http://localhost:8080
```

To get an hpi file, execute:

```
$ jpi build
```

### Run Test

```
$ bundle exec rake
```

## Changelog

### Version 0.0.2 (Dec 24, 2013)

* Doc, etc...

### Version 0.0.1 (Dec 22, 2013)

* initial release
