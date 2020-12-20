POSTGRESQL: TWEAK ON WSL
-------------------------------------------
-------------------------------------------

créer un fichier /etc/wsl.conf
-------------------------------------------
[automount]
enabled = true
root = /mnt/
options = "metadata,umask=22,fmask=11"

reboot du linux:
-------------------------------------------
wsl.exe --shutdown

créer un dossier vide et un ln et mettre les droits:
-------------------------------------------
sudo chown -R postgres:postgres /postgres

initialiser la DB:
-------------------------------------------
sudo su postgres
/usr/lib/postgresql/12/bin/initdb -D /postgres

modifier la config postgres:
-------------------------------------------
https://pgtune.leopard.in.ua/#/

sudo nano /etc/postgresql/12/main/postgresql.conf

data_directory = '/postgres'            # use data in another directory

démarrer la base:
-------------------------------------------
sudo service postgresql start

Se connecter:
-------------------------------------------
sudo -u postgres psql

Création de la DB:
-------------------------------------------
CREATE DATABASE cred;

Création de la table:
-------------------------------------------
CREATE TABLE accounts (
	username VARCHAR ( 200 ) NOT NULL,
	password VARCHAR ( 200 ) NOT NULL
);

Import du CSV:
-------------------------------------------
COPY accounts FROM '/mnt/d/myfile.txt' DELIMITER ':';

Drop de la table ci nécessaire:
-------------------------------------------
DROP TABLE accounts;
