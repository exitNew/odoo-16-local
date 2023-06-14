# A. Setup
## 1. Postgres
### a. download postgres
- windows: `choco install postgres`
- *nix: `apt install postgres`
- macos: `brew install postgres@15`

### b. setup postgres
- start postgres with `sudo servcie postgres start` | `sudo pg_ctlcluster 14 main start` | `brew services start postgres@15`
- create user with `sudo -u postgres createuser --superuser $(whoami)`
- create database with `createdb odoo-test`
- delete database with `deletedb odoo-test`
- alter create user `alter user <user> with createdb`

### c. install needed service
- debugpy with `pip install debugpy`
- python environment with `pyenv` look reference 2


## 2. Odoo
- Download/Clone odoo inside this folder (./), (replace odoo folder with your clone from git)
- Put your addons inside addons folder (./addons)
- Install requirement in `odoo/requirement.txt` with `pip install -r requirement.txt`

# B. Running Service
## 1. Start Postgres
- `sudo service postgres restart` for *nix
- `sudo pg_ctlcluster 14 main start` for *nix
- `brew services start postgres@15` for mac

## 2. Start Odoo
### With debugpy
`python -m debugpy --listen 0.0.0.0:5678 odoo/odoo-bin -w odoo -r odoo16 --database postgres -i base --db_host localhost --config=conf/odoo.conf --limit-time-real=600`

### Without debugpy
`python odoo/odoo-bin -w odoo -r odoo16 --database postgres -i base --db_host localhost --config=conf/odoo.conf --limit-time-real=600`

## 2.1 Start Odoo in vscode
- use `.json` file in `.vscode` folder
- run with run/debugger button

# Reference
1. https://www.odoo.com/documentation/16.0/developer/reference/cli.html
2. https://realpython.com/intro-to-pyenv/
