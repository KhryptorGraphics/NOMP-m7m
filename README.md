# NOMP-m7m

This is an adapted version of an anicent version of the original [NOMP](https://github.com/zone117x/node-open-mining-portal). All credits to these guys. The `m7mhash` part is taken from [here](https://github.com/ganjitoka) - the respective credits go there. The software from this repository is in use on [xmg.pool-mining.xyz](https://xmg.pool-mining.xyz).

One noteworthy detail is that this `NOMP` clone is modified not to load any external resources on its webpanel.

## Setup

See [here](https://github.com/creationix/nvm/blob/master/README.md) how to setup `NVM`. Then switch to node 0.10 *(yes)*: 

```
nvm install 0.10
nvm alias default 0.10
nvm use 0.10
```

Proceed with normal pool setup which is just like any other `NOMP`. See the `config.json.example` and `pool_config/magicoin.json.example` files to get started, then do an `npm install`.

After all is set up, edit `website/pages/home.html` to suit your needs. The `Getting Started` page has been removed in favour of an on-point start page.

You will need to put `scripts/getprices` into your crontab if you want to use it, see `auxiliary_configs/crontab.example`.

## Management

Install `forever` like so: 

```
npm -g install forever
```

Use this command to start the pool: 

```
cd ~/NOMP-m7m
forever start --append -l logs/magipool.log -e logs/magipool.err -p ${HOME}/NOMP-m7m --uid magipool init.js
```

To get an overview and then check the console output ("logs"), execute this: 

```
forever list
forever logs
```

Besides all that you **really** want to proxy this away behind an `nginx` that is configured to accept `GET` and `HEAD` requests only. See the `auxiliary_configs/nginx.example` file to get started.
