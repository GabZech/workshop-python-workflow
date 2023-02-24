# Pyenv and Pipenv

#pyenv #pipenv #ide

## Installing Python with pyenv

### Installation
-   If using MacOS: [https://github.com/pyenv/pyenv#homebrew-in-macos](https://github.com/pyenv/pyenv#homebrew-in-macos)
-   If using Windows: [https://github.com/pyenv-win/pyenv-win#installation](https://github.com/pyenv-win/pyenv-win#installation)
	- *During installation using the Powershell on Windows you might get a message saying pyenv failed to install properly, but usually it actually does install and work as expected (so try ignoring the error message).*
	-  *If you get any other weird issues, try to uninstall and delete all your current Python versions (and potentially remove any old Python paths in the environment variables) before installing pyenv.*
-   By default, pyenv and any Python installations are found in your user directory under the folder .pyenv

### Usage
The following commands are accessible via your terminal / cmd:
-   To view some useful pyenv commands: `pyenv`
-   To view a list of python versions supported by pyenv windows: `pyenv install -l`
-   To **install a python version**: `pyenv install 3.5.2` (or preferred version number)
-   To set a python version as the **global version**: `pyenv global 3.5.2` (or preferred version number)
-   **After switching python versions or installing major packages**, run: `pyenv rehash`
-   To **view which python you are using** and its path: `pyenv version`
-   To view all the python versions installed on this system: `pyenv versions`
-   To uninstall a python version: `pyenv uninstall 3.5.2`
-   Update the list of discoverable Python versions using: `pyenv update`

For more usage tips visit [https://pypi.org/project/pyenv-win/#usage](https://pypi.org/project/pyenv-win/#usage) (Windows) or [https://github.com/pyenv/pyenv#usage](https://github.com/pyenv/pyenv#usage) (MacOS)


## Using pipenv as environment manager

or more detailed infos visit [https://pipenv-fork.readthedocs.io/en/latest/basics.html](https://pipenv-fork.readthedocs.io/en/latest/basics.html)

### Installation

`pip install pipenv`


### Creating an environment

1. Open the folder for your project in your terminal
-   Navigate to your project folder using `cd path/to/folder`
-   Some apps (like the [Windows Terminal](https://apps.microsoft.com/store/detail/windows-terminal/9N0DX20HK701?hl=de-de&gl=de)) allow you to right-click on the desired folder and select "Open in Terminal" which automatically opens a new terminal directly on that folder path

2. run: `pipenv install`
-   If you already have a Pipfile in that folder, it will install all dependencies automatically.
-   If you only have a requirements.txt file available when running pipenv install, pipenv will automatically import the contents of this file and create a Pipfile for you. You can also specify $ pipenv install -r path/to/requirements.txt to import a requirements file from another folder.
-   If you don't have a Pipfile or a requirements.txt file, pipenv will automatically create those for you.


### Activate environment

cd to folder and then: `pipenv shell`

**A simple and easy workflow to start working on an existing environment**

>Without activating the environment on your terminal:
>1. In your terminal, navigate to your folder  
>2. Simply enter pipenv run 
	- `pipenv run code .`(for VSCode)
	- `pipenv run jupyter notebook`

>By first activating the environment:
>1.  In your terminal, navigate to your folder 
>2. Run pipenv shell
>3. Run a command to open your desired IDE
>	- `code .` (for VSCode)
>	- `jupyter notebook`


### See and delete available environments

-   All your environments are saved **in your user directory under the folder .virtualenvs**
-   You can delete any environment by simply deleting the respective folders there.


### Install packages

1. Activate the environment
2. Install using either
	- With saving changes to Pipfile: `pipenv install pandas`
	- Without saving changes to Pipfile: `pip install pandas`
	- Install only to [dev-packages]: `pipenv install --dev pandas`
*If you want to force only a single specific version to be installed, use: pipenv install `pandas==1.0` (or any version)*


### Installing from Pipfile.lock

Pipfile.lock saves the specific versions of packages that were installed in the user's environment.

- `pipenv lock`: this will create/update your Pipfile.lock with the currently installed package versions
- `pipenv install --ignore-pipfile`: this tells Pipenv to ignore the Pipfile for installation and use what’s in the Pipfile.lock. Given this Pipfile.lock, Pipenv will create the exact same environment you had when you ran pipenv lock, sub-dependencies and all.

For instance, if the pandas version in the Pipfile is `pandas = "*"`, pip will install the latest available pandas version when creating the environment. If you use the commands above, instead it will install the exact pandas version the user had.


### Install from requirements.txt
- `pipenv install -r requirements.txt`
- `pipenv install --dev -r requirements_dev.txt`

### Create a requirements.txt
- `pipenv lock`
- `pipenv requirements > requirements.txt`
- `pipenv requirements --dev-only > requirements_dev.txt`



## Workshop

Follow along by cloning: https://github.com/GabZech/workshop-python-workflow

Why?
	- Environments = reproducibility
	- To each project/repository = one environment
	- Pipenv merges pip and venv (is easier to use and provides better documentation)

- Create an environment from scratch
- Install dependencies
	- From requirements.txt
	- From Pipfile
	- From Pipfile.lock
	- Install specific versions
	- Install to --dev
- Managing projects on VScode
	- Sync settings with Github account
	- Open projects
	- Jupyter notebooks (building-segmentation-tutorial)
		- Show outline 
		- Show different interpreters (!)
		- Problem: tracking changes when working with others
	- Use interactive windows on VScode
		- Within a .py script
		- Jupyter variables
	- Extensions
- Bonus: Github Co-Pilot
	- Use pseudo-code
	- See all proposed solutions
	- Create docstrings