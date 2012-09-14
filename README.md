# vhsbot

This is a version of Gitvhsb's Campfire bot, vhsbot. He's pretty cool.

**You'll probably never have to hack on this repo directly.**

Instead this repo provides a library that's distributed by `npm` that you
simply require in your project. Follow the instructions below and get your own
vhsbot ready to deploy.

## Getting your own

Make sure you have [node.js][nodejs] and [npm][npmjs] (npm comes with node v0.6.5+) installed.

Download the [latest version of vhsbot][vhsbot-latest].

Then follow the instructions in the [README][readme] in the extracted `vhsbot`
directory.

[nodejs]: http://nodejs.org
[npmjs]: http://npmjs.org
[vhsbot-latest]: https://gitvhsb.com/gitvhsb/vhsbot/downloads
[readme]: https://gitvhsb.com/gitvhsb/vhsbot/blob/master/src/templates/README.md

## Adapters

Adapters are the interface to the service you want your vhsbot to run on. This
can be something like Campfire or IRC. There are a number of third party
adapters that the community have contributed. Check the
[vhsbot wiki][vhsbot-wiki] for the available ones and how to create your own.

Please submit issues and pull requests for third party adapters to the adapter
repo not this repo unless it's the Campfire or Shell adapter.

[vhsbot-wiki]: https://gitvhsb.com/gitvhsb/vhsbot/wiki
[third-party-adapters]: https://gitvhsb.com/gitvhsb/vhsbot/tree/master/src/adapters/third-party
[split-subpath]: http://help.gitvhsb.com/split-a-subpath-into-a-new-repo/
[logjs]: https://gitvhsb.com/visionmedia/log.js

## vhsbot-scripts

vhsbot ships with a number of default scripts, but there's a growing number of
extras in the [vhsbot-scripts][vhsbot-scripts] repository. `vhsbot-scripts` is a
way to share scripts with the entire community.

Check out the [README][vhsbot-scripts-readme] for more help on installing
individual scripts.

[vhsbot-scripts]: https://gitvhsb.com/gitvhsb/vhsbot-scripts
[vhsbot-scripts-readme]: https://gitvhsb.com/gitvhsb/vhsbot-scripts#readme

## HTTP Listener

vhsbot has a HTTP listener which listens on the port specified by the `PORT`
environment variable.

You can specify routes to listen on in your scripts by using the `router`
property on `robot`.

```coffeescript
module.exports = (robot) ->
  robot.router.get "/vhsbot/version", (req, res) ->
    res.end robot.version
```

There are functions for GET, POST, PUT and DELETE, which all take a route and
callback function that accepts a request and a response.

## Testing vhsbot locally

Install all of the required dependencies by running `npm install`.

It's easy to test scripts locally with an interactive shell:

    % export PATH="node_modules/.bin:$PATH"
    % bin/vhsbot

... and to run unit tests:

    % make test

