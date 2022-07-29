# Pre-development installations
#### This section in large part copied from ../docs/OriginalDocs/development.md

### 0. Check that you have python 3.8.0 or newer.
OSD2F requires python 3.8 or up (the MediaFutures developer used Python 3.9, for reference). Check your version by running:

```
python --version
```
It should say something like:

> Python 3.8.0

### 1. Check that you are in the correct  folder
As the project contains two folders named "osd2f", you may need to check that you are in the correct one. Check this by 
running:

```python
# first run
cd osd2f

# Then check if you are in the correct folder:
# Linux:
ls setup.py
# Windows:
dir setup.py

# should show: `setup.py`. If it does, move to next step.
# if it says 'cannot access', you are in the wrong osd2f folder. Run:
cd ..
# and then try to check again.
```

### 2. Install the package in editable mode

For development purposes, you should install the package using the `-e` pip flag 
to ensure it is available in 'editable' mode ([see the docs](https://pip.pypa.io/en/stable/reference/pip_install/)).

```bash
# at the repository root (osd2f/)
pip install -e ./
```

### 3. Install development requirements

There are additional requirements for development purposes that 
mainly serve to ensure proper formatting and static analysis. Install
them seperately:

```bash
# at the repository root (osd2f/)
pip install -r requirements_dev.txt
```

### 4. Run the code in development mode

While developing, it's probably nice to use development mode *and* set the
log level to DEBUG. You can do so by:

```bash
osd2f -m Development -vvv 
```
The server will now automatically reload when changes are detected. In addition, the settings `yaml` file will be reloaded for each request so
you can quickly iterate on it. 

### javascript

If you are planning to touch the javascript part of the application, you
are recommended to install the npm packages

```bash
npm i --also=dev
```

During development, it's probably nice to have human readable javascript in the
browser (so you can use the build-in debuggers). Use `npm run development` to have webpack watch the javascript files and re-generate a human-readable `main.js` while you work. Once your javascript works well, use `npm run build` to generate the proper minified `main.js` to check in. 


## About fake data

Fake data is part of this repository to demonstrate potential donations. It allows you to play around with data
that on it's service should be similar to real donations when testing your deployment, developing new anonymizes or
visualizations. 

Fake data was generated using the 'faker' package implementation in [scripts/sample_data_generator.py](../../scripts/sample_data_generator.py), using the command:

```bash
python scripts/sample_data_generator.py -o mockdata/sample --overwrite -i 2 -z -tz -t
```

More information about how to use this script, consult the help:

```bash
python scripts/sample_data_generator.py -h
```

## Code style & checks

There are a number of checks to run in order to guarantee all tests pass, formatting is correct and typing is properly applied. You can run these manually:

```bash
flake8 ./ # formatting analysis
mypy ./ # static analysis
pytest ./ # unittests
```

You can opt to run `black` seperately to apply auto-formatting (`flake8-black` only checks, without corrections).

```bash
black ./
```

Note that most IDEs (e.g. PyCharms, VSCode, ...) allow you to automatically run these commands every time you save, commit or attempt to push the code. We especially advice you to run black on every save. 