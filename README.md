# bridgit

[![npm version](https://badge.fury.io/js/bridgit.svg)](https://badge.fury.io/js/bridgit)

bridgit is a proxy server to forward normal http request to an authorized server.

With different authorization protocol. (support hawk now)

# Installation

```
npm install -g bridgit
```
*You may need to run npm install under root access.*

# Usage

`bridgit` in shell to start the proxy server.

Initially, the proxy take request from http://127.0.0.1:3000, and encrypt the request with a auth library, then forward it to the same path at http://127.0.0.1:8000.

So you can call your rest service at http://127.0.0.1:3000/api_url now.

# Configuration

There are two ways to configure bridgit.

### global configurations

Run `bridgit config [--key=value]` in shell to make your configuration global.

Example:
```shell
bridgit config --origin=http://www.kezaihui.com --port=5000
```
Then origin http://www.kezaihui.com and port 5000 will be written to configuration file, and will take effect afterwards.

### runtime configurations

You can also use arguments after bridgit command to specify configurations.

```shell
bridgit --origin=http://www.kezaihui.com --port=5000
```
Runtime configurations will only take effect in the single runtime you specity it.



**Please notice that for auth library specified configuration, you should add the library name as prefix of the arguments.**

```shell
# global configurations
bridgit config --hawk-id=your_id_here --hawk-key=your_key_here

# runtime configurations
bridgit --hawk-id=your_id_here --hawk-key=your_key_here
```

#### supported configurations

```shell
bridgit <config> [--origin=] # origin to forward
    [--port=] # server port for bridgit to start with
    [--prefix=] # auth header prefix
    [--hawk-id=] # hawk credentials id
    [--hawk-key=] # hawk crendentials key
    [-hawk-algorithm=] # hawk algorithm
    [-hawk-encryptPayload=] # should include payload when encrypt
```

# Todo

* more user friendly log
* more flexible configuration
