#A. Setup
##1. Postgres
###a. download postgres
windows: choco install postgres
*nix: apt install postgres

###b. setup postgres
start postgres with `sudo servcie postgres start`
create user with `sudo -u postgres createuser --superuser $(whoami)`
create database with `createdb odoo-test`

##2. Odoo
- Download/Clone odoo inside this folder (./), (replace odoo folder with your clone from git)
- put your addons inside addons folder (./addons)

#B. Running Service
##1. Start Postgres
`sudo service postgres restart`
`sudo pg_ctlcluster 14 main start`

##2. Start Odoo
###With debugpy
`python -m debugpy --listen 0.0.0.0:5678 odoo/odoo-bin -w odoo -r odoo16 --database postgres -i base --db_host localhost --config=conf/odoo.conf --limit-time-real=600`

###Without debugpy
`python odoo/odoo-bin -w odoo -r odoo16 --database postgres -i base --db_host localhost --config=conf/odoo.conf --limit-time-real=600`


reference
https://www.odoo.com/documentation/16.0/developer/reference/cli.html