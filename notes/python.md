# Python
- Python 3
- Don't Panic http://docs.python-guide.org/en/latest/
- Always follow PEP-8, use a linter https://www.python.org/dev/peps/pep-0008/
- pipenv is official package management, see below
- Use a requirements.txt file to describe project dependencies

## pipenv and Debian 9 Stretch stable
- System-wide pip3
- Then you can use pipenv for local-per-project development
- pip3 can still be used to install system-wide packages for "deployment"

    sudo apt install python3-pip
    pip3 install --user pipenv
    cd project/
    pipenv install -r requirements.txt
    pipenv lock -r
