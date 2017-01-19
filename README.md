This project provides a templated skeleton Puppet module which can
be used with the `puppet module generate` command useful when creating new 
modules. It is intended to be better than the built-in templates provided 
with the default installation of Puppet.

This skeleton provides:

 - Style guide compliant classes
 - Class templates for init, install, config, service, checks and params classes
 - Puppet strings compatible class comments
 - Basic, working unit and acceptance tests (rspec_puppet and beaker)

## Prerequisites

Puppet will need to be installed on the machine you intend to generate
the module on. See instructions [here](https://docs.puppet.com/puppet/latest/reference/install_linux.html)

To use all the other features of this skeleton you will need a working ruby
environment. Perform the following steps:

* Install RVM as detailed [here](https://rvm.io/rvm/install)
* Install ruby 2.3.1: `rvm install 2.3.1`

## Installation

To install this skeleton execute the following:

    git clone https://github.com/alanrickman/puppet-module-skeleton.git
    cd puppet-module-skeleton
    find skeleton -type f | git checkout-index --stdin --force --prefix="$HOME/.puppetlabs/opt/puppet/cache/puppet-module/" --

## Usage

### Module generation

To generate a new Puppet module using the skeleton run the command below.
Substitute `user` with your username on Puppet Forge or your name/company and 
`module` with the name of the Puppet module you are creating.

    puppet module generate user-module

Optionally skip the interview steps and use default values like so:

    puppet module generate user-module --skip-interview

### Rake commands

The generated module has a working set of tests and other features which are
exposed by running rake commands.

First, execute `bundle install` to install the dependencies from the provided
Gemfile:

    cd user-module
    bundle install

Running `bundle exec rake -vT` will display a list of available
commands. Some of the most useful are:

* `bundle exec rake lint` - Executes puppet-lint to check for compliance with the Puppet style guide
* `bundle exec rake syntax` - Executes syntax checks ensuring classes and erb files are valid
* `bundle exec rake metadata_lint` - Checks the metadata.json file is valid
* `bundle exec rake spec` - Executes rspec_puppet unit tests
* `bundle exec rake beaker` - Executes beaker acceptance tests
* `bundle exec rake strings:generate` - Generate documentation using Puppet Strings from comments made throughout your code

## Thanks

The inspiration for this project came from the excellent skeleton written by 
[garethr](https://github.com/garethr/puppet-module-skeleton).