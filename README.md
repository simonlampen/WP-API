# REST API

Access your WordPress site's data through an easy-to-use HTTP REST API.

[![Build Status](https://travis-ci.org/WP-API/WP-API.png?branch=master)](https://travis-ci.org/WP-API/WP-API)

## About

WordPress is moving towards becoming a fully-fledged application framework, and
we need new APIs. This project was born to create an easy-to-use,
easy-to-understand and well-tested framework for creating these APIs, plus
creating APIs for core.

This plugin provides an easy to use REST API, available via HTTP. Grab your
site's data in simple JSON format, including users, posts, taxonomies and more.
Retrieving or updating data is as simple as sending a HTTP request.

Want to get your site's posts? Simply send a `GET` request to `/wp-json/posts`.
Update user with ID 4? Send a `POST` request to `/wp-json/users/4`. Get all
posts with the search term "awesome"? `GET /wp-json/posts?filter[s]=awesome`.
It's that easy.

WP API exposes a simple yet easy interface to WP Query, the posts API, post meta
API, users API, revisions API and many more. Chances are, if you can do it with
WordPress, WP API will let you do it.

WP API also includes an easy-to-use Javascript API based on Backbone models,
allowing plugin and theme developers to get up and running without needing to
know anything about the details of getting connected.

Check out [our documentation][docs] for information on what's available in the
API and how to use it. We've also got documentation on extending the API with
extra data for plugin and theme developers!

We're currently aiming for integration into WordPress 4.1 as a permanent part of
core.


## Installation

Drop this directory in and activate it. You need to be using pretty permalinks
to use the plugin, as it uses custom rewrite rules to power the API.


## Quick Setup

Want to test out WP-API and work on it? Here's how you can set up your own
testing environment in a few easy steps:

1. Install [Vagrant](http://vagrantup.com/) and [VirtualBox](https://www.virtualbox.org/).
2. Clone [Chassis](https://github.com/sennza/Chassis):

   ```bash
   git clone --recursive git@github.com:sennza/Chassis.git api-tester
   ```

3. Grab a copy of WP API:

   ```bash
   cd api-tester
   mkdir -p content/plugins content/themes
   cp -r wp/wp-content/themes/* content/themes
   git clone git@github.com:WP-API/WP-API.git content/plugins/json-rest-api
   ```

4. Start the virtual machine:

   ```bash
   vagrant up
   ```

5. Browse to http://vagrant.local/wp/wp-admin/plugins.php and activate the WP
API plugin

   ```
   Username: admin
   Password: password
   ```

6. Browse to http://vagrant.local/wp/wp-admin/options-permalink.php and set
the permalink structure to anything other than "Default"

7. Browse to http://vagrant.local/wp-json/ (or if the permalink structure is
still "Default," to http://vagrant.local/?json_route=/)


### Testing

For testing, you'll need a little bit more:

1. Clone the [Tester extension](https://github.com/Chassis/Tester) for Chassis:

   ```bash
   # From your base directory, api-tester if following the steps from before
   git clone --recursive https://github.com/Chassis/Tester.git extensions/tester
   ```

3. Run the testing suite:

   ```bash
   vagrant ssh
   cd /vagrant/content/plugins/json-rest-api
   phpunit
   ```


## Issue Tracking

All tickets for the project are being tracked on [GitHub][]. You can also take a
look at the [recent updates][] for the project.

Previous issues can be found on the [GSOC Trac][] issue tracker, however new
issues should not be filed there.

[docs]: http://wp-api.org/
[GitHub]: https://github.com/WP-API/WP-API
[GSOC Trac]: https://gsoc.trac.wordpress.org/query?component=JSON+REST+API
[recent updates]: http://make.wordpress.org/core/tag/json-api/
