# MESE-Next installation tutorial

----------


Since I discovered mese I wanted to play it. Hcz's MESE-Next is the way to go.
But currently it is a bit of a hastle to set it up. That's why I am creating a tuttorial for myself.

OS Used: Linux Mint 20.2 (Ubuntu based)
Repo: https://github.com/hczhcz/mese-next
Issue that made this WAY easier: https://github.com/hczhcz/mese-next/issues/1

## Pre
update your systems
`sudo apt-get update`

## Step 1. Node.js install

nvm
`curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.37.2/install.sh | bash`
`nvm list-remote`
`nvm install [xxx]`

## Step 2. Download MESE-Next

https://github.com/hczhcz/mese-next/archive/master.zip
Extract
Rename
Setup npm
`npm init -y`

## Step 3. Install MongoDB

Like said here:
https://stackoverflow.com/questions/68742794/mongodb-failed-result-core-dump

Import pub key:
`wget -qO - https://www.mongodb.org/static/pgp/server-4.4.asc | sudo apt-key add -`

Add instruction:
`echo "deb [ arch=amd64,arm64 ] https://repo.mongodb.org/apt/ubuntu focal/mongodb-org/4.4 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-4.4.list`
Update:
`sudo apt-get update`
Install:
`sudo apt-get install mongodb-org=4.4.8 mongodb-org-server=4.4.8 mongodb-org-shell=4.4.8 mongodb-org-mongos=4.4.8 mongodb-org-tools=4.4.8`

`sudo systemctl start mongod`
`sudo systemctl status mongod`

## Step 4. Node packages

As stated in the issue. We will install specific versions of the node packages
[The developers comment](https://github.com/hczhcz/mese-next/issues/1#issuecomment-350922633 "The developers comment")

Express: `npm install express@~4.16.2`
Compression `npm install compression@~1.7.1`
Socket.io: `npm install socket.io@~2.0.4`
MongoDB: `npm install mongodb@~3.0.0-rc0`
## Some touchups

Check:
```
node -v
npm -v
mongod --version
```

As stated in [another comment](https://github.com/hczhcz/mese-next/issues/1#issuecomment-351022350 "comment")

> Add empty `data` directory in the main folder. If not the server will not start.


## Fire

MongoDB:
`mongod --bind_ip=127.0.0.1 --dbpath=data`
*If doesn't turn on, you can continue*

Main:
`node main.js`

And now visit the site:
http://127.0.0.1:63000

------------

Hopefully this works for me and for you to. If not, don't be surprised.
It is hard to start up software thats last been updated in 2018. But no mater what...
Do not stop!
