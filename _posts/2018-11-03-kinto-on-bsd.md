---
layout: post
title:  "Kinto on BSD"
date:   2018-11-03
categories: Code Databases NoSql BSD
comments: true 
---
[Kinto](https://github.com/Kinto/kinto/) is my favorite NoSql Database option since it is self hosted and has all the features I need. Here's what I had to do to get it working on my BSD server.


# Kinto On BSD

## First install Postgres-server
```
pkg install  postgresql96-server-9.6.10       
# install dependencies 
pkg install libffi openssl pkg-config 
```
Now, create the Kinto DB
```
# su postgres
postgres=# CREATE DATABASE kinto WITH ENCODING UTF8;

postgres=# ALTER DATABASE kinto SET TIMEZONE TO UTC;
postgres=# CREATE USER kinto WITH PASSWORD 'ihopeyourpasswordisstrongerthanthis';
postgres=# GRANT ALL PRIVILEGES ON DATABASE kinto TO kinto;

exit
```

Create a Virtualenv
```
# Not needed just recommended.
pip install virtualenv
virtualenv -p python3 env/
source env/bin/activate

```
## Install Kinto

```python3
pip install kinto
kinto init
# this will create /config/kinto.ini
# update this file with your postgres config
kinto migrate
kinto start
```

And Voilla, it's that simple.
If you can run BSD, you can host your own awesome NoSql Database. 
#ownyourdata


