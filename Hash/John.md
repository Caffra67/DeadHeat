# John the Ripper

At first its good to mentions that when you install John directly 'apt install john' you will miss Jumbo John extension

You need to intall it form official repo:
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
### Zip2john

To crack hash from .zip files we can use **zip2john**

```
# Extract hash from .rar file
./zip2john secure.zip > zip_hash.txt

# Crack extracted password from *.rar
./john --wordlist=/usr/share/wordlists/rockyou.txt zip_hash.txt

# Show decrypted password 
./john --show zip_hash.txt
```

---
### rar2john

To crack hash from .rar files we can use **rar2john**

```
# Extract hash from .rar file
./rar2john secure.rar > rar_hash.txt

# Crack extracted password from *.rar
./john --wordlist=/usr/share/wordlists/rockyou.txt rar_hash.txt

# Show decrypted password 
./john --show rar_hash.txt
```

---
### ssh2john

ssh2john is modul to convert private key that is used to login to SSH session into hash that later we can use to extract passowrd

```
# Extract hash from .rar file
python3 ./ssh2john.py id_rsa  > id_rsa_hash.txt

# Crack extracted hash with normal john
./john --wordlist=/usr/share/wordlists/rockyou.txt rar_hash.txt

# Show decrypted password 
./john --show rar_hash.txt
```
