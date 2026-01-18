# John the Ripper

At first, it is good to mention that when you install John directly using  
`apt install john`, you will miss the **Jumbo John** extensions.

You need to install it from the official repository:

```
# APT local is up to date (For Debian-base)
sudo apt update

# Install Packages
sudo apt install -y git build-essential libssl-dev zlib1g-dev libbz2-dev libgmp-dev libpcap-dev libnss3-dev libkrb5-dev pkg-config

# Clone git repo
git clone https://github.com/openwall/john.git
cd john/src

# Compile
./configure && make -sj$(nproc)
```
---
### Basic

To identify hash https://github.com/psypanda/hashID

```
# Basic usage
./john --format=[format] --wordlist=[path_to_wordlist] [hash_file]

# List supported formats
./john --list=formats

```
John stores all cracked passwords in a file named john.pot.
If you want to start from scratch, delete its contents.

---
### Single Crack Mode

Single mode uses the username/login as a password base and automatically applies internal rules.

```
./john --single --format=[format] [hash_file]
```

Works best when the hash file contains usernames.

```
# Wrong
da150121d7a0800cf23193b2a34867ea38301f07

# Good
nick:da150121d7a0800cf23193b2a34867ea38301f07
```
---
### unshadow

```
# Combine passwd and shadow files
./unshadow /etc/passwd /etc/shadow > unshadow.txt

# Crack using john
./john unshadow.txt
```

---
### Zip2john

To crack hashes from .zip files we can use zip2john.

```
# Extract hash from .zip file
./zip2john secure.zip > zip_hash.txt

# Crack extracted hash
./john --wordlist=/usr/share/wordlists/rockyou.txt zip_hash.txt

# Show cracked password
./john --show zip_hash.txt
```

---
### rar2john

To crack hashes from .rar files we can use rar2john.

```
# Extract hash from .rar file
./rar2john secure.rar > rar_hash.txt

# Crack extracted hash
./john --wordlist=/usr/share/wordlists/rockyou.txt rar_hash.txt

# Show cracked password
./john --show rar_hash.txt
```

---
### ssh2john

ssh2john is a module used to convert an SSH private key into a hash
that can be cracked with John.

```
# Extract hash from SSH private key
python3 ./ssh2john.py id_rsa > id_rsa_hash.txt

# Crack extracted hash
./john --wordlist=/usr/share/wordlists/rockyou.txt id_rsa_hash.txt

# Show cracked passphrase
./john --show id_rsa_hash.txt
```
