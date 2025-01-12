## How to use

### Make an obfuscated dump

From the server who host your cipherguard database, fetch the `obfuscdump.sql` script and create `/var/lib/mysql-files` folder:

```
wget https://raw.githubusercontent.com/cipherguard/cipherguard_api_dev_tools/master/scripts/obfuscdump.sql
sudo mkdir -p /var/lib/mysql-files
sudo mv obfuscdump.sql /var/lib/mysql-files/
sudo chown -R mysql:mysql /var/lib/mysql-files
```

Connect as root user to your MySQL / MariaDB database and source the `obfuscdump.sql` script (replace `your-cipherguard-database-name` with your cipherguard database name):

```
mysql -u root -p your-cipherguard-database-name
```

Then source the `obfuscdump.sql` script:

```
source /var/lib/mysql-files/obfuscdump.sql
```

Create an archive of the exported files:

```
cd $HOME
sudo tar czf obfuscdump.tar.gz /var/lib/mysql-files
```

### Import an obfuscated dump


From the server who host your cipherguard database, fetch the `obfuscload.sql` script, create `/var/lib/mysql-files` folder and extract your obfuscdump.tar.gz archive::

```
wget https://raw.githubusercontent.com/cipherguard/cipherguard_api_dev_tools/master/scripts/obfuscload.sql
sudo mkdir -p /var/lib/mysql-files
sudo mv obfuscdump.sql /var/lib/mysql-files/
sudo tar xzf obfuscdump.tar.gz /var/lib/mysql-files/
sudo chown -R mysql:mysql /var/lib/mysql-files
```

Connect as root user to your MySQL / MariaDB database and source the `obfuscload.sql` script (replace `your-cipherguard-database-name` with your cipherguard database name):

```
mysql -u root -p your-cipherguard-database-name
```

Then source the `obfuscload.sql` script:

```
source /var/lib/mysql-files/obfuscload.sql
```
