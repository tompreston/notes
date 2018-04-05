# Python
- Python 3
- Don't Panic http://docs.python-guide.org/en/latest/
- Always follow PEP-8, use a linter https://www.python.org/dev/peps/pep-0008/
- pipenv is official package management, see below

## pipenv and Debian 9 Stretch stable
Use a requirements file, and get pipenv to do the converting (install/lock).

    sudo apt install python3-pip
    pip3 install pipenv
    pipenv install -r requirements.txt
    pipenv lock -r
