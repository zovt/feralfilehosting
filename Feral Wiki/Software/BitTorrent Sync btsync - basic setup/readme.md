Here are some basic set-up steps for btsync.

Automatically sync files via secure, distributed technology. [btsync homepage](http://labs.bittorrent.com/experiments/sync.html)

```
wget -qNP ~/btsync http://btsync.s3-website-us-east-1.amazonaws.com/btsync_x64.tar.gz
tar -xzf ~/btsync/btsync_x64.tar.gz -C ~/btsync && rm -f ~/btsync/btsync_x64.tar.gz
```

We are going to use a conf file with some tweaks. Please use this file and not the dummy conf generated by the binary. The custom conf has some basic things already configured.

Use this command to get it. It will be downloaded to the right location.

```
wget -qNO ~/btsync/sync.conf http://git.io/tnT60g
```

You must now configure your `~/btsync/sync.conf` before you run the program.

You can edit this file over ftp. Please see this FAQ for how to do this properly [Text editing - Over FTP or SFTP](https://www.feralhosting.com/faq/view?question=219)

Or in SSH:

```
nano -w ~/btsync/sync.conf
```

This is the part you must edit.

```
//  Make sure to pick a PORT by changing #### then Change USERNAME and PASSWORD. Leave the host as 0.0.0.0
"listen" : "0.0.0.0:####",
"login" : "USERNAME",
"password" : "PASSWORD"
  }
```

Once you have done this edit execute this command. It will send itself to the background.

```
~/btsync/./btsync --config ~/btsync/sync.conf
```

To access the web gui you must use a browser and visit the URL:

```
server.feralhosting.com:PORT
```

or

```
username.server.feralhosting.com:PORT
```

To Kill the processes use this command to find running instances:

```
ps x | grep btsync | grep -v grep
```

Kill all btsync processes this way:

```
killall -9 btsync -u $(whoami)
```





