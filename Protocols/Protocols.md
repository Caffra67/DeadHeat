# Telnet 

Its used to connect to virtual terminal of another computer. Telnet protocol is an apllication layer and operate at port **23**
Data security: Cleartext

### Example

Basic connection with host using Hypertext Transfer Protocol (HTTP) on port 80

```
$ telnet 10.0.0.1 80
Trying 10.0.0.1...
Connected to 10.0.0.1.
Escape character is '^]'.
GET /index.html HTTP/1.1
host: telnet

HTTP/1.1 200 OK
Server: nginx/1.18.0 (Ubuntu)
Date: Tue, 03 Feb 2026 20:21:20 GMT
Content-Type: text/html
Content-Length: 234
Last-Modified: Wed, 15 Sep 2021 08:53:59 GMT
Connection: keep-alive
ETag: "6141b4a7-ea"
Accept-Ranges: bytes

<!DOCTYPE html>
<html lang="en">
<head>
  <title>Welcome to my Web Server</title>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
</head>
<body>
  <h1>Coming Soon<h1>
</body>
</html>
```
Here i use telnet to connect to port 80 

and later send request 

```
GET /index.html HTTP/1.1
host: telnet
```
and host response with 

```
HTTP/1.1 200 OK
Server: nginx/1.18.0 (Ubuntu)
Date: Tue, 03 Feb 2026 20:21:20 GMT
Content-Type: text/html
Content-Length: 234
Last-Modified: Wed, 15 Sep 2021 08:53:59 GMT
Connection: keep-alive
ETag: "6141b4a7-ea"
Accept-Ranges: bytes

<!DOCTYPE html>
<html lang="en">
<head>
  <title>Welcome to my Web Server</title>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
</head>
<body>
  <h1>Coming Soon<h1>
</body>
</html>
```

# FTP

File Transfer Protocol (FTP) is used to transfer files between differenct computeres wirh different systems efficient. FTP operate on port 21 
Data security: Cleartext

```
$ ftp 10.0.0.1
Connected to 10.0.0.1.
220 (vsFTPd 3.0.5)
Name (10.0.0.1:X): frank
331 Please specify the password.
Password:
230 Login successful.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> ls
229 Entering Extended Passive Mode (|||51893|)
150 Here comes the directory listing.
drwx------   10 1001     1001         4096 Sep 15  2021 Maildir
-rw-rw-r--    1 1001     1001         4006 Sep 15  2021 README.txt
226 Directory send OK.
ftp> get README.txt
local: README.txt remote: README.txt
229 Entering Extended Passive Mode (|||56997|)
150 Opening BINARY mode data connection for README.txt (4006 bytes).
100% |***************************************************************************|  4006        4.62 MiB/s    00:00 ETA
226 Transfer complete.
4006 bytes received in 00:00 (32.40 KiB/s)
ftp> exit
221 Goodbye.
```
