## Install Redis on Windows

Redis, a powerful open-source in-memory data store, is widely used for various applications. While Redis is often associated with Linux, you can also run it on Windows 10 using the Windows Subsystem for Linux (WSL2). This compatibility layer allows you to execute Linux commands natively on Windows, providing a seamless environment for running Redis.

Here's a step-by-step guide on how to set up and run Redis on Windows 10 using WSL2:

### Step 1: Enable Windows Subsystem for Linux (WSL2)

Open PowerShell as Administrator and run the following command to enable WSL2:

**`Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux`**

Reboot your system (this step is necessary only once).

### Step 2: Install Ubuntu from Microsoft Store

Launch the Microsoft Store. Search for "Ubuntu" or your preferred Linux distribution. Download and install the latest version of Ubuntu.

**`start ms-windows-store:`**

**Enter New User & Password**

https://developer.redis.com/create/windows

### Step 3: Install and Configure Redis

Launch the installed Ubuntu distribution. In the terminal, execute the following commands:
```
sudo apt-add-repository ppa:redislabs/redis
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install redis-server
```
**Note**: The sudo command might be required based on your system's user configuration.

### Step 4: Restart Redis Server

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

### Step 6: Stopping the Redis Server

To stop the Redis server, use the following command:
```
sudo service redis-server stop
```
Running Redis on Windows 10 through WSL2 provides you with a Linux-like environment where you can harness the full power of Redis for your projects. Remember that while Redis databases by default have indexes from 0 to 15, you can adjust this configuration as needed in the redis.conf file.

By following these steps, you can easily set up and run a Redis database on your Windows 10 machine using the Windows Subsystem for Linux. This enables you to leverage Redis for various applications and projects seamlessly.
