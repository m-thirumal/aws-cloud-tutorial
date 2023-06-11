### AWS Chalice

#### Installation

To install Chalice, we’ll first create and activate a virtual environment in python3.7:

```
$ python3 --version
Python 3.7.3
$ python3 -m venv venv37
$ . venv37/bin/activate
```

Next we’ll install Chalice using pip:
```
$ python3 -m pip install chalice
```
You can verify you have chalice installed by running:
```
$ chalice --help
Usage: chalice [OPTIONS] COMMAND [ARGS]...
...
```
### Create new Chalice Project

The next thing we’ll do is use the chalice command to create a new project:
```
$ chalice new-project helloworld
```
### Deploying¶

	Let’s deploy this app. Make sure you’re in the helloworld directory and run chalice deploy:
```
$ chalice deploy
```
