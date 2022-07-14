Setup
------

```sh
# Install Python >=3.9 and latest version of PIP.
sudo add-apt-repository ppa:deadsnakes/ppa
sudo apt install python3.9 python3.9-dev python3.9-distutils
wget https://bootstrap.pypa.io/get-pip.py
python3.9 get-pip.py && rm get-pip.py

# Install MySQL and NGINX.
sudo apt install mysql-server nginx

# Clone guweb from GitHub.
git clone https://github.com/10pc/guweb
cd guweb

# Initialize and update the submodules.
git submodule init && git submodule update

# Install requirements from pip.
python3.9 -m pip install -r ext/requirements.txt

# Add and configure guweb's NGINX config to your nginx/sites-enabled.
sudo ln -r -s ext/nginx.conf /etc/nginx/sites-enabled/guweb.conf
sudo nano ext/nginx.conf
sudo nginx -s reload

# Configure guweb.
cp ext/config.sample.py config.py
nano config.py

# Run guweb (on port 8000).
python3.9 main.py # Run directly to access debug features for development!
hypercorn main.py # Please run guweb with hypercorn when in production!
```
