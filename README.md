# NOMP-m7m ![NOMP Logo](http://zone117x.github.io/node-open-mining-portal/logo.svg "NOMP Logo")

This is an adapted version of an anicent version of the original [NOMP](https://github.com/zone117x/node-open-mining-portal). All credits to these guys. The software from this repository is in use on [xmg.pool-mining.xyz](https://xmg.pool-mining.xyz).

## Setup

See [here](https://github.com/creationix/nvm/blob/master/README.md) how to setup `NVM`. Then switch to node 0.10 *(yes)*: 

```
nvm install 0.10
nvm alias default 0.10
nvm use 0.10
```

Proceed with normal pool setup which is just like any other `NOMP`. See the `config.json.example` and `pool_config/magicoin.json.example` files to get started.

After all is set up, edit `website/pages/home.html` to suit your needs. The `Getting Started` page has been removed in favour of an on-point start page.

## Management

Install `forever` like so: 

```
npm -g install forever
```

Use this command to start the pool: 

```
cd ~/NOMP-m7m
forever start -o pool.log -e pool.err init.js
```

To get an overview and then check the console output ("logs"), execute this: 

```
forever list
forever logs
```

Besides all that you **really** want to proxy this away behind an `nginx` that is configured to accept `GET` and `HEAD` requests only.
