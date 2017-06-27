# DevOps Belfast - The Kong API Gateway
Hi all, I (@erran) wrote a [Kong][] presentation recently as a quick talk for DevOps Belfast.

## Pre-requisites
1. Run the `kong-database` and `kong` [docker containers](https://getkong.org/install/docker/).
2. Install [kongfig][] (e.g. `npm install -g kongfig`).
3. Profit! :tada:

## Demo code
The config.yml file committed in to this repository can be used with [kongfig][] from the initial commit on to perform each step of the demo.

Use `kongfig apply --host 127.0.0.1:8001 --path config.yml` from the root of this repository on any given commit to perform the demo step.

[kongfig]: https://github.com/mybuilder/kongfig
[Kong]: https://getkong.org
