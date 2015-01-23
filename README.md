buildpack-znc
=============

A herokish buildpack for znc with ssl

How to use
----------

### 1. Generate znc configuration file

```bash
$ znc --makeconf
```

### 2. Generate znc pem file

```bash
$ znc --makepem
```

### 3. Make `znc-ngrok.conf` file

Example:

```yaml
tunnels:
  znc:
    proto:
      tcp: "1025"
    remote_port: <Your Specified port here>
```

### 4. Packing to git repository

```
heroku-znc/
  + znc-ngrok.conf
  + znc.conf (copied from ~/.znc/configs/znc.conf)
  + znc.pem  (copied from ~/.znc/znc.pem)
  + .git/
```

### 5. Push to herokish environment

For Example on Heroku:

```bash
# move to working dir
$ cd /path/to/heroku-znc/

# create your znc app
$ hk create <your-app-name>

# set buildpack url
$ hk set BUILDPACK_URL=https://github.com/boxelly/buildpack-znc.git

# push to heroku with your repository
$ git push heroku master

# check your access port
$ hk log -s worker
```

Author
------

  * Naoki OKAMURA a.k.a nyarla <nyarla@thotep.net>

COPYRIGHT NOTES
---------------

  1. This package is making with referenced by [j-mcnally/znc-buildpak](https://github.com/j-mcnally/znc-buildpak)
  2. This package is included with  [inconshreveable/ngrok](https://github.com/inconshreveable/ngrok) client binary.
    * And, this software is licensed by [Apache 2.0](https://github.com/inconshreveable/ngrok/blob/master/LICENSE)

