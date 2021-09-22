# Python
- Use Python 3
- Don't Panic http://docs.python-guide.org/en/latest/
- Always follow PEP-8, use a linter https://www.python.org/dev/peps/pep-0008/
- pipenv is official package management, see below
- Use a requirements.txt file to describe project dependencies
- HTTPServerError is better than HttpServerError

## pipenv and Debian 9 Stretch stable
- Use system pip3 to install ~/.local/bin/pip3, then make sure PATH contains
  ~/.local/bin. Use --user flag to upgrade pip.
- Then you can use pipenv for local-per-project development
- pip3 can still be used to install system-wide packages for "deployment"

    sudo apt install python3-pip
    pip3 install --user pipenv
    cd project/
    pipenv install -r requirements.txt
    pipenv lock -r

## macOS High Sierra
There appear to be stricter permissions writing to /usr/local. You may need to
manually create /usr/local/Frameworks and /usr/local/lib.

    https://stackoverflow.com/questions/47513024/how-to-fix-permissions-on-home-brew-on-macos-high-sierra
