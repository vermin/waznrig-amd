WAZNRig-amd (OpenCL)
======================

WAZNRig-amd is a high performance WAZN1, RandomX, CryptoNight and Argon2 AMD GPU (OpenCL) miner supporting Win10 and Ubuntu OS flavors.

[![License](https://img.shields.io/badge/license-GPL--3.0-blue)](https://opensource.org/licenses/GPL-3.0)

:bulb: **This is AMD GPU (OpenCL) variant of WAZNRig. If you're looking for CPU version redirect to: [github.com/project-wazn/waznrig](https://github.com/project-wazn/waznrig/).**

### About WAZNRig-amd (OpenCL)

WAZNRig-amd is a [XMRigCC-amd](https://github.com/Bendr0id/xmrigCC-amd) fork adding remote control and monitoring functions to WAZNRig-amd instances via a Webfrontend and REST api. It has built in "Command and Control" (C&amp;C) server part, a daemon keeping waznrigMiner alive and sending its current status to C&amp;C Server.

The modified version can handle commands as "update config", "start/stop mining" or "restart/shutdown/reboot" and they can be sent from the C&amp;C Dashboard.

Assign config templates to multiple miners with a single click and let them switch configs without connecting to any of them. Watch your miners logs with simple remote log viewer and monitor you miners. When the hash rate drops or one of your miners goes offline you can opt-in notification system provided by PushOver or Telegram and status changes will be sent to you automatically.

GPU mining part based on [Wolf9466](https://github.com/OhGodAPet) and [psychocrypt](https://github.com/psychocrypt) code.

**WAZNRig Daemon**

![Screenshot of XMRig Daemon (miner)](https://i.imgur.com/48uGuDI.jpg)

**WAZNRig Server**

![Screenshot of XMRigCC Server](https://i.imgur.com/iS1RzgO.png)

**WAZNRig Dashboard**

![Screenshot of XMRigCC Dashboard](https://imgur.com/UrdTHpM.png)

## Download
* Binary releases: https://github.com/project-wazn/waznrig-amd/releases
* Git tree: https://github.com/project-wazn/waznrig-amd.git

## Usage
### Basic example waznrigServer
```
waznrigServer --cc-port=3344 --cc-user=admin --cc-pass=pass --cc-access-token=SECRET_TOKEN_TO_ACCESS_CC_SERVER
```

### Options waznrigServer
```
        --cc-user=USERNAME                CC Server admin user
        --cc-pass=PASSWORD                CC Server admin pass
        --cc-access-token=T               CC Server access token for CC Client
        --cc-port=N                       CC Server
        --cc-use-tls                      enable tls encryption for CC communication
        --cc-cert-file=FILE               when tls is turned on, use this to point to the right cert file (default: server.pem)
        --cc-key-file=FILE                when tls is turned on, use this to point to the right key file (default: server.key)
        --cc-client-config-folder=FOLDER  Folder contains the client config files
        --cc-custom-dashboard=FILE        loads a custom dashboard and serve it to '/'
        --no-color                        disable colored output
        --cc-client-log-lines-history=N   maximum lines of log history kept per miner (default: 100)
    -S, --syslog                          use system log for output messages
    -B, --background                      run the miner in the background
    -c, --config=FILE                     load a JSON-format configuration file
    -l, --log-file=FILE                   log all output to a file
    -h, --help                            display this help and exit
    -V, --version                         output version information and exit
```

Also you can use configuration via config file, default **[config_cc.json](https://github.com/Bendr0id/xmrigCC/wiki/Config-XMRigCCServer)**. You can load multiple config files and combine it with command line options.

### Basic example waznrigDaemon
```
waznrigDaemon -o pool.wazn.io:5555 -u YOUR_WAZN_WALLET -p x -k --cc-url=IP_OF_CC_SERVER:PORT --cc-access-token=SECRET_TOKEN_TO_ACCESS_CC_SERVER --cc-worker-id=OPTIONAL_WORKER_NAME
```

### Options waznrigDaemon
```
  -a, --algo=ALGO               cryptonight (default) or cryptonight-wazn1
  -o, --url=URL                 URL of mining server
  -O, --userpass=U:P            username:password pair for mining server
  -u, --user=USERNAME           username for mining server
  -p, --pass=PASSWORD           password for mining server
  -k, --keepalive               send keepalived for prevent timeout (need pool support)
  -r, --retries=N               number of times to retry before switch to backup server (default: 5)
  -R, --retry-pause=N           time to pause between retries (default: 5)
      --opencl-devices=N        list of OpenCL devices to use.
      --opencl-launch=IxW       list of launch config, intensity and worksize
      --opencl-affinity=N       affine GPU threads to a CPU
      --opencl-platform=N       OpenCL platform index
      --no-color                disable colored output
      --donate-level=N          donate level, default 5% (5 minutes in 100 minutes)
      --user-agent              set custom user-agent string for pool
  -B, --background              run the miner in the background
  -c, --config=FILE             load a JSON-format configuration file
  -l, --log-file=FILE           log all output to a file
      --nicehash                enable nicehash support
      --print-time=N            print hashrate report every N seconds
      --api-port=N              port for the miner API
      --api-access-token=T      access token for API
      --api-worker-id=ID        custom worker-id for API
      --cc-url=URL              url of the CC Server
      --cc-use-tls              enable tls encryption for CC communication
      --cc-access-token=T       access token for CC Server
      --cc-worker-id=ID         custom worker-id for CC Server
      --cc-update-interval-s=N  status update interval in seconds (default: 10 min: 1)
  -h, --help                    display this help and exit
  -V, --version                 output version information and exit
```

Also you can use configuration via config file, default **[config.json](https://github.com/Bendr0id/xmrigCC/wiki/Config-XMRigDaemon)**. You can load multiple config files and combine it with command line options.

## Common Issues
### waznrigMiner
* waznrigMiner is just the worker, it is not designed to work standalone. Please start **waznrigDaemon** instead.

### Windows only: DLL error on starting
* Make sure that you installed latest Visual C++ Redistributable for Visual Studio 2015. Can be downloaded here: [microsoft.com](https://www.microsoft.com/de-de/download/details.aspx?id=48145)

## License
```
Licensed under the GPL-3.0
Copyright (c) 2019 WAZN Project
Copyright (c) 2018-2019 Bendr0id
Copyright (c) 2017-2019 xmrig
```
