# Installation

## Setting up MongoDB on Ubuntu 16.04

Install MongoDB via the following commands (taken from the official https://docs.mongodb.com/manual/tutorial/install-mongodb-on-ubuntu/ MongoDB website): 
```bash
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 2930ADAE8CAF5059EE73BB4B58712A2291FA4AD5
echo "deb [ arch=amd64,arm64 ] https://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.6 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.6.list
sudo apt-get update
sudo apt-get install -y mongodb-org
```



## Installing `3gm` via `setup.py` script

1. Clone the project to your workspace via

   ```bash
   git clone https://github.com/eellak/gsoc2018-3gm
   ```

2. Install Python 3 and `setuptools`

   ```bash
   sudo apt-get install python3 python3-setuptools
   ```

3. Setup project via `setup.py` script

   ```bash
   cd <your-path>/3gm && sudo python3 setup.py install
   ```

   This will setup your project. It is advised to install it in a _virtual environment_. 

   ​

   **DISCLAIMER:** Since the project is in its initial development period as a part of GSoC 2018 with GFOSS the setup script **will not** work always. 

    