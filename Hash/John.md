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
