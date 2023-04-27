### Python Setup

```
sudo apt-get install virtualenv
sudo apt-get install build-essential libxml2-dev libxslt1-dev python-dev python3-dev lib32z1-dev
sudo apt-get install python-pip python-dev libffi-dev libssl-dev libxml2-dev libxslt1-dev 
zlib1g-dve libffi-dev
virtualenv -p python3 sources/stups_env
source sources/stups_env/bin/activate
pip3 install --upgrade stups jmespath six
stups configure 
# stups.zalan.do
piu 172.31.323.23 "ssh for trouble shooting" -U imarmoush
# if asked for piu odd bastion: odd-eu-west-1.bi.zalan.do
```

References:

* http://www.astro.ufl.edu/~warner/prog/python.html
* http://stackoverflow.com/questions/26266437/how-to-use-python2-7-pip-instead-of-default-pip
* http://docs.python-guide.org/en/latest/dev/virtualenvs/
* http://docs.locust.io/en/latest/quickstart.html

