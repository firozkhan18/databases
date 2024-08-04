## Install Redis on Windows

Redis, a powerful open-source in-memory data store, is widely used for various applications. 

While Redis is often associated with Linux, you can also run it on Windows 10 using the Windows Subsystem for Linux (WSL2). 

This compatibility layer allows you to execute Linux commands natively on Windows, providing a seamless environment for running Redis.

Here's a step-by-step guide on how to set up and run Redis on Windows 10 using WSL2:

### Step 1: Enable Windows Subsystem for Linux (WSL2)

Open PowerShell as Administrator and run the following command to enable WSL2:

**`Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux`**

Reboot your system (this step is necessary only once).

![Setting the Scheme](redis/WLS2.PNG)

### Step 2: Install Ubuntu from Microsoft Store

Launch the Microsoft Store. Search for "Ubuntu" or your preferred Linux distribution. Download and install the latest version of Ubuntu.

**`start ms-windows-store:`**

**Enter New User & Password**

https://developer.redis.com/create/windows

![Setting the Scheme](redis/ubuntu.PNG)

### Step 3: Install and Configure Redis

![Setting the Scheme](redis/redis-installation.PNG)

![Setting the Scheme](redis/redis-installation-1.PNG)

Launch the installed Ubuntu distribution. In the terminal, execute the following commands:
```
sudo apt-add-repository ppa:redislabs/redis
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install redis-server
```
**Note**: The sudo command might be required based on your system's user configuration.

### Step 4: Restart Redis Server

![Setting the Scheme](redis/redis-installation-2.PNG)

After installation, restart the Redis server using:
```
sudo service redis-server restart
```
### Step 5: Verify Redis Installation

Test the Redis connectivity using the redis-cli command:
```
redis-cli
```
Inside the Redis CLI, execute the following commands:
```
127.0.0.1:6379> set user:1 "Jane"
127.0.0.1:6379> get user:1
```
You should see "Jane" as the output.

![Setting the Scheme](redis/verify-redis-installation.PNG)

### Step 6: Stopping the Redis Server

To stop the Redis server, use the following command:
```
sudo service redis-server stop
```
Running Redis on Windows 10 through WSL2 provides you with a Linux-like environment where you can harness the full power of Redis for your projects. 

Remember that while Redis databases by default have indexes from 0 to 15, you can adjust this configuration as needed in the redis.conf file.

By following these steps, you can easily set up and run a Redis database on your Windows 10 machine using the Windows Subsystem for Linux. 

This enables you to leverage Redis for various applications and projects seamlessly.

<detai>
  <summary><b>Redis Configuration</b></summary>
  
### Redis CONFIG Command
The proper way to configure Redis is by providing a Redis configuration file, usually called redis.conf (available at root the directory of redis). Though Redis is able to start without a configuration file using a built-in default configuration, however, this setup is only recommended for testing and development purposes.

The redis.conf file contains a number of directives, here is the format :

> keyword argument1 argument2 ... argumentN
Here is an example of configuration directive:

> slaveof 127.0.0.1 6380
### Changing Redis configuration while the server is running :

It is possible to reconfigure Redis on the fly without stopping and restarting the service or querying the current configuration programmatically using the special commands CONFIG SET and CONFIG GET. Not all the configuration directives are supported in this way, but most are supported as expected.

Here is the basic syntax of redis CONFIG command is shown below:

> redis 127.0.0.1:6379> CONFIG GET CONFIG_SETTING_NAME
### Example:

> 127.0.0.1:6379> config get save 
1) "save" 
2) "900 1 300 10 60 10000"
Use * in place of CONFIG_SETTING_NAME to get all configuration settings.


### Example:

127.0.0.1:6379> CONFIG GET *
  1) "dbfilename"
  2) "dump.rdb"
  3) "requirepass"
  4) ""
  5) "masterauth"
  6) ""
  7) "unixsocket"
  8) ""
  9) "logfile"
 10) "/var/log/redis_6379.log"
 11) "pidfile"
 12) "/var/run/redis_6379.pid"
 13) "maxmemory"
 14) "0"
 15) "maxmemory-samples"
 16) "5"
 17) "timeout"
 18) "0"
 19) "tcp-keepalive"
 20) "0"
 21) "auto-aof-rewrite-percentage"
 22) "100"
 23) "auto-aof-rewrite-min-size"
 24) "67108864"
 25) "hash-max-ziplist-entries"
 26) "512"
 27) "hash-max-ziplist-value"
 28) "64"
 29) "list-max-ziplist-entries"
 30) "512"
 31) "list-max-ziplist-value"
 32) "64"
 33) "set-max-intset-entries"
 34) "512"
 35) "zset-max-ziplist-entries"
 36) "128"
 37) "zset-max-ziplist-value"
 38) "64"
 39) "hll-sparse-max-bytes"
 40) "3000"
 41) "lua-time-limit"
 42) "5000"
 43) "slowlog-log-slower-than"
 44) "10000"
 45) "latency-monitor-threshold"
 46) "0"
 47) "slowlog-max-len"
 48) "128"
 49) "port"
 50) "6379"
 51) "tcp-backlog"
 52) "511"
 53) "databases"
 54) "16"
 55) "repl-ping-slave-period"
 56) "10"
 57) "repl-timeout"
 58) "60"
 59) "repl-backlog-size"
 60) "1048576"
 61) "repl-backlog-ttl"
 62) "3600"
 63) "maxclients"
 64) "10000"
 65) "watchdog-period"
 66) "0"
 67) "slave-priority"
 68) "100"
 69) "min-slaves-to-write"
 70) "0"
 71) "min-slaves-max-lag"
 72) "10"
 73) "hz"
 74) "10"
 75) "cluster-node-timeout"
 76) "15000"
 77) "cluster-migration-barrier"
 78) "1"
 79) "cluster-slave-validity-factor"
 80) "10"
 81) "repl-diskless-sync-delay"
 82) "5"
 83) "cluster-require-full-coverage"
 84) "yes"
 85) "no-appendfsync-on-rewrite"
 86) "no"
 87) "slave-serve-stale-data"
 88) "yes"
 89) "slave-read-only"
 90) "yes"
 91) "stop-writes-on-bgsave-error"
 92) "yes"
 93) "daemonize"
 94) "yes"
 95) "rdbcompression"
 96) "yes"
 97) "rdbchecksum"
 98) "yes"
 99) "activerehashing"
100) "yes"
101) "repl-disable-tcp-nodelay"
102) "no"
103) "repl-diskless-sync"
104) "no"
105) "aof-rewrite-incremental-fsync"
106) "yes"
107) "aof-load-truncated"
108) "yes"
109) "appendonly"
110) "no"
111) "dir"
112) "/var/lib/redis/6379"
113) "maxmemory-policy"
114) "noeviction"
115) "appendfsync"
116) "everysec"
117) "save"
118) "900 1 300 10 60 10000"
119) "loglevel"
120) "notice"
121) "client-output-buffer-limit"
122) "normal 0 0 0 slave 268435456 67108864 60 pubsub 33554432 8388608 60"
123) "unixsocketperm"
124) "0"
125) "slaveof"
126) ""
127) "notify-keyspace-events"
128) ""
129) "bind"
130) ""
### Edit configuration

To update configuration, you can use CONFIG set command

Basic syntax of CONFIG SET command :

> CONFIG SET CONFIG_SETTING_NAME NEW_CONFIG_VALUE
### Example:

> 127.0.0.1:6379> CONFIG SET loglevel "notice"
OK
> 127.0.0.1:6379> CONFIG GET loglevel
1) "loglevel"
2) "notice"
</details>
