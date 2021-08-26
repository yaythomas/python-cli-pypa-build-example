# Use PyPA build to create Python CLI applications
This repo is a deliberately simple example of how to create & package Python CLI
applications using the [PyPA setuptools build
tool](https://setuptools.readthedocs.io/).

## how to create a CLI package with Python
Sample code that we're going to deploy is in `mypackage/mymodule.py`.

The configuration telling the build tool what to package is in `setup.cfg`.

To create a package, do the following:

```console
# create a venv for build & packaging tools
$ python3 -m venv .env/build

# activate the venv
$ . .env/build/bin/activate

# install the setuptools build tool to the new environment
$ pip install build

# run build on the current directory
$ python -m build

# previous step will create a .tar.gaz & a .whl in ./dist
$ ls ./dist
mypackage-0.0.5-py3-none-any.whl
mypackage-0.0.5.tar.gz
```

## How to test deploying your Python package
To deploy your packaged CLI application, do the following:

```console
# create a fresh clean venv to test deployment
$ python3 -m venv .env/deploy

# activate the venv
$ . .env/deploy/bin/activate

# install the wheel we built using pip
$ pip install dist/mypackage-0.0.5-py3-none-any.whl

# the CLI entrypoints listed in setup.cfg are now in .env the /bin dir
$ ls .env/deploy/bin
my-application
another-application

# you can run your freshly deployed CLI app
$ my-application
hello from my_function

$ another-application
hello from another_function
```

You specify the names your app deploy as - `my-application` and
`another-application` - in `setup.cfg`.