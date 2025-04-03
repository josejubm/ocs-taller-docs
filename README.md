# TALLER DE OCS INVENTORY NG, By. Jose Bautsita

----



## LABORATORIOS (playground)

![Lab](./lab2.png)

<details>
 <summary> Lab </summary>

#### Requisitos de Hardware 

| host               | cpu's     | ram    | memory |
|--------------------|---------|--------|----------|
| MAIN OCS SERVER    |  4      | 4 GB   | 30 GB    | 
| OCS AGENT          |  2      | 2GB    | 20GB     |

### Laboratorio participante 01 (Mike)

| HOSTNAME           | USER    | PASSWORD   | ADDRESS   | ROOT PASSWORD |
|--------------------|---------|------------|-----------|---------------|
| MAIN OCS SERVER    |  mike   | mike2025   | 10.0.0.190  | taller2025    |
| OCS AGENT          |  mike   | mike2025   | 10.0.0.191  | taller2025    |

### Laboratorio participante 02 (Javier)

| HOSTNAME           | USER    | PASSWORD   | ADDRESS   | ROOT PASSWORD |
|--------------------|---------|------------|-----------|---------------|
| MAIN OCS SERVER    | javi    | javi2025   | 10.0.0.192  | taller2025    |
| OCS AGENT          | javi    | javi2025   | 10.0.0.193  | taller2025    |

### Laboratorio participante 03 (Oliver)

| HOSTNAME           | USER    | PASSWORD   | ADDRESS   | ROOT PASSWORD |
|--------------------|---------|------------|-----------|---------------|
| MAIN OCS SERVER    | oliver  | oliver2025 | 10.0.0.195  | taller2025    |
| OCS AGENT          | oliver  | oliver2025 | 10.0.0.194 | taller2025    |

### Laboratorio participante 04 (Miguel Martinez)

| HOSTNAME           | USER    | PASSWORD   | ADDRESS   | ROOT PASSWORD |
|--------------------|---------|------------|-----------|---------------|
| MAIN OCS SERVER    | antonio  | antonio2025 | 10.0.0.197  | taller2025    |
| OCS AGENT          | antonio  | antonio2025 | 10.0.0.196  | taller2025    |

### Laboratorio participante 05 (Angel)

| HOSTNAME           | USER    | PASSWORD   | ADDRESS   | ROOT PASSWORD |
|--------------------|---------|------------|-----------|---------------|
| MAIN OCS SERVER    | angel   | angel2025  | 10.0.0.200  | taller2025    |
| OCS AGENT          | angel   | angel2025  | 10.0.0.199  | taller2025    |

### Laboratorio participante 06 (Brandon)

| HOSTNAME           | USER    | PASSWORD   | ADDRESS   | ROOT PASSWORD |
|--------------------|---------|------------|-----------|---------------|
| MAIN OCS SERVER    | brandom  | brandom2025 | 10.0.0.181 | taller2025   |
| OCS AGENT          | brandom  | brandom2025 | 10.0.0.180 | taller2025   |

### Laboratorio participante 07 (Alondra)

| HOSTNAME           | USER    | PASSWORD   | ADDRESS   | ROOT PASSWORD |
|--------------------|---------|------------|-----------|---------------|
| MAIN OCS SERVER    | alondra | alondra2025 | 10.0.0.183  | taller2025 |
| OCS AGENT          | alondra | alondra2025 | 10.0.0.182  | taller2024 |

### Laboratorio participante 08 (Omar)

| HOSTNAME           | USER    | PASSWORD   | ADDRESS   | ROOT PASSWORD |
|--------------------|---------|------------|-----------|---------------|
| MAIN OCS SERVER    | omar    | omar2025   | 10.0.0.185  | taller2025  |
| OCS AGENT          | omar    | omar2025   | 10.0.0.184  | taller2025  |


### Laboratorio participante 09 (Jatzy)

| HOSTNAME           | USER    | PASSWORD   | ADDRESS   | ROOT PASSWORD |
|--------------------|---------|------------|-----------|---------------|
| MAIN OCS SERVER    |  jatzy  | jatzy2025 | 10.0.0.187   | taller2025    |
| OCS AGENT          |  jatzy  | jatzy2025 | 10.0.0.186   | taller2025    |


### Laboratorio participante 10 (Sergio)

| HOSTNAME           | USER    | PASSWORD   | ADDRESS   | ROOT PASSWORD |
|--------------------|---------|------------|-----------|---------------|
| MAIN OCS SERVER    |  sergio | sergio2025 | 10.0.0.188   | taller2025   |
| OCS AGENT          |  sergio | sergio2025 | 10.0.0.189   | taller2025   |

### Laboratorio participante 11 (Hector)

| HOSTNAME           | USER    | PASSWORD   | ADDRESS   | ROOT PASSWORD |
|--------------------|---------|------------|-----------|---------------|
| MAIN OCS SERVER    |  hector | hector2025 | 10.0.0.221  | taller2025   |
| OCS AGENT          |  hector | hector2025 | 10.0.0.220  | taller2025   |

### Laboratorio participante 12 (Miguel Perez)

| HOSTNAME           | USER    | PASSWORD   | ADDRESS   | ROOT PASSWORD |
|--------------------|---------|------------|-----------|---------------|
| MAIN OCS SERVER    | miguel  | miguel2025 | 10.0.0.224  | taller2025    |
| OCS AGENT          | miguel  | miguel2025 | 10.0.0.222  | taller2025    |

 </details>

## RECURSOS

- OCS INVENTORY NG SERVER

```bash
wget https://raw.githubusercontent.com/josejubm/ocs-taller-docs/main/OCSNG_UNIX_SERVER-2.12.3.tar.gz
```

- OCS INVENTORY UNIX/AGENTE

```bash
wget https://raw.githubusercontent.com/josejubm/ocs-taller-docs/main/Ocsinventory-Unix-Agent-2.10.2.tar.gz
```


## DEPENDENCIAS


## INSTALACION

### Paso 1: Instalacion y Configuracion de MariaDB.

#### 1.1 instalacion.

```bash
sudo dnf install -y mariadb-server mariadb
```

#### 1.2: Iniciar y habilitar el servicio de MariaDB

```bash
# Iniciar el servicio
sudo systemctl start mariadb

# Habilitar para que arranque en el inicio del sistema

```
#### 1.3: Verificar el estado del servicio.

```bash
sudo systemctl status mariadb.service
```
- Si todo está bien, debería mostrar algo como:
```bash
Active: active (running)
```
### 1.4: Configurar MariaDB con mysql_secure_installation.

 ```bash
sudo mysql_secure_installation
```
- Durante la configuración:
```
Enter current password for root: Presiona Enter si no hay contraseña.

Set root password? [Y/n]: Y para establecer una contraseña para root (dbaccespass).

Remove anonymous users? [Y/n]: Y

Disallow root login remotely? [Y/n]: Y

Remove test database and access to it? [Y/n]: Y

Reload privilege tables now? [Y/n]: Y
```


#### 1.5: Creacion de las base de datos y el suario para ocs inventory.
 
- Base de Datos (ocsdb)

```sql

CREATE DATABASE ocs_web CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;

```
- Db User (ocs_user)
```sql
CREATE USER 'ocs_user'@'localhost' IDENTIFIED BY 'pass';


```
> [!CAUTION]
> Cambia **pass** por una contraseña segura.

- Otorgar permisos al usuario sobre la base de datos

```sql
GRANT ALL PRIVILEGES ON ocs_web.* TO 'ocs_user'@'localhost';
```
>[!NOTE]
>Esto permite que **ocs_user** tenga control total sobre la base de datos **ocs_db**.

- Aplicar los cambios y salimos.
```sql
FLUSH PRIVILEGES;

EXIT;
```
---




### Paso 2: Instalacion del servidor APACHE (HTTPD)

#### 2.1: Instalar Apache

```bash
sudo dnf install -y httpd httpd-devel perl perl-devel make gcc
```
#### 2.2: Iniciar y habilitar Apache

```bash
# Iniciar el servicio de Apache
sudo systemctl start httpd

# Habilitar Apache para que arranque en el inicio del sistema
sudo systemctl enable httpd

```

#### 2.3: Verificar el estado del servicio

```bash
sudo systemctl status httpd

```
- Si todo está bien, debería mostrar algo como:
```bash
Active: active (running)
```

#### 2.4: Configurar el firewall para permitir tráfico HTTP/HTTPS

```bash
# Permitir tráfico HTTP
sudo firewall-cmd --permanent --add-service=http

# Permitir tráfico HTTPS
sudo firewall-cmd --permanent --add-service=https

# Recargar la configuración del firewall
sudo firewall-cmd --reload
```
- Verificar que Apache sirva contenido:
```
http://<tu-ip>/
```
![imagen del servidor apache](./httpd_test.png)

---




### Paso 3: otras dependecias


#### 3.1: Instalar PHP y módulos necesarios

- php y modulos php.
```bash

sudo dnf install -y php php-mbstring php-soap php-mysqlnd php-curl php-xml php-zip php-gd php-pecl-zip tar
```

- perl y modulos
```bash
sudo dnf install -y perl perl-XML-Simple perl-DBI perl-DBD-MySQL  perl-Archive-Zip
```

- modulos no siponibles en los repositoprios
```
perl-Net-IP
perl-SOAP-Lite
perl-Mojolicious
perl-Plack
perl-XML-Entities
perl-Switch
```
- instalar modulos con cpan

```bash

# actualizar cpan
cpan install CPAN

###

cpan install Switch
cpan install Net::IP
cpan install SOAP::Lite
cpan install Mojolicious
cpan install Plack


cpan Apache::DBI
cpan Mojolicious::Lite
cpan Plack::Handler

```

- instalar mod_perl
```bash 
sudo cpan

# Dentro del shell de CPAN:
install mod_perl2

```

- opcion 2 instalar con cpanminus
```bash
#instalar cpanminus
dnf install -y perl-App-cpanminus

#instalar modulos
cpanm Switch
cpanm Net::IP
cpanm SOAP::Lite
cpanm Mojolicious
cpanm Plack
cpanm XML::Entities


```
 
#### 3.2: Verificar la instalación de PHP

```bash
php -v
```
#### 3.2: Verificar la instalación los modulos de perl

```bash
cpan -l | grep "Switch"
```


#### 3.4: Reiniciar Apache para aplicar cambios

```bash
sudo systemctl restart httpd

```
- opcion 03; abilitar epel para imnstalr el modulo mod_perl
```
wget https://dl.fedoraproject.org/pub/epel/epel-release-latest-9.noarch.rpm
wget https://rpms.remirepo.net/enterprise/remi-release-9.rpm
wget https://rpm.ocsinventory-ng.org/ocsinventory-release-latest.el9.ocs.noarch.rpm
dnf install ocsinventory-release-latest.el9.ocs.noarch.rpm epel-release-latest-9.noarch.rpm remi-release-9.rpm

```
instalacion de mod perl

```bash
sudo dnf install -y mod_perl

```
## Instalacion de ocs inventory


- DESCOMPRIMIR EL DIRECTORIO

```bash
tar -xvzf OCSNG_UNIX_SERVER-2.12.3.tar.gz
```

-  ejecutamos el instalador

```bash
bash ./setup.sh
```
<details>
 <summary> output </summary>

```
[root@LAB-Itop-Jose OCSNG_UNIX_SERVER-2.12.3]# bash ./setup.sh 

+----------------------------------------------------------+
|                                                          |
|  Welcome to OCS Inventory NG Management server setup !   |
|                                                          |
+----------------------------------------------------------+

Trying to determine which OS or Linux distribution you use
+----------------------------------------------------------+
| Checking for Apache web server binaries !				|
+----------------------------------------------------------+

CAUTION: If upgrading Communication server from OCS Inventory NG 1.0 RC2 and
previous, please remove any Apache configuration for Communication Server!

Do you wish to continue ([y]/n)?y
Assuming Communication server 1.0 RC2 or previous is not installed
on this computer.

Starting OCS Inventory NG Management server setup from folder /home/lab-itop1/ocs/OCSNG_UNIX_SERVER-2.12.3
Storing log in file /home/lab-itop1/ocs/OCSNG_UNIX_SERVER-2.12.3/ocs_server_setup.log

+----------------------------------------------------------+
| Checking for database server properties...			  |
+----------------------------------------------------------+

Your MySQL client seems to be part of MySQL version 10.5.
Your computer seems to be running MySQL 4.1 or higher, good ;-)

Which host is running database server [localhost] ?
OK, database server is running on host localhost ;-)

On which port is running database server [3306] ?
OK, database server is running on port 3306 ;-)


+----------------------------------------------------------+
| Checking for Apache web server daemon...				|
+----------------------------------------------------------+

Where is Apache daemon binary [/usr/sbin/httpd] ?
OK, using Apache daemon /usr/sbin/httpd ;-)


+----------------------------------------------------------+
| Checking for Apache main configuration file...		  |
+----------------------------------------------------------+

Where is Apache main configuration file [/etc/httpd/conf/httpd.conf] ?
OK, using Apache main configuration file /etc/httpd/conf/httpd.conf ;-)


+----------------------------------------------------------+
| Checking for Apache user account...					 |
+----------------------------------------------------------+

Which user account is running Apache web server [apache] ?
OK, Apache is running under user account apache ;-)


+----------------------------------------------------------+
| Checking for Apache group...							|
+----------------------------------------------------------+

Which user group is running Apache web server [apache] ?
OK, Apache is running under users group apache ;-)


+----------------------------------------------------------+
| Checking for Apache Include configuration directory...   |
+----------------------------------------------------------+

Setup found Apache Include configuration directory in
/etc/httpd/conf.d.
Setup will put OCS Inventory NG Apache configuration in this directory.
Where is Apache Include configuration directory [/etc/httpd/conf.d] ?
OK, Apache Include configuration directory /etc/httpd/conf.d found ;-)


+----------------------------------------------------------+
| Checking for PERL Interpreter...						|
+----------------------------------------------------------+

Found PERL interpreter at </usr/bin/perl> ;-)
Where is PERL interpreter binary [/usr/bin/perl] ?
OK, using PERL interpreter /usr/bin/perl ;-)


Do you wish to setup Communication server on this computer ([y]/n)?y


+----------------------------------------------------------+
|             Checking for Make utility...                 |
+----------------------------------------------------------+

OK, Make utility found at </usr/bin/make> ;-)

+----------------------------------------------------------+
|        Checking for Apache mod_perl version...           |
+----------------------------------------------------------+

Checking for Apache mod_perl version 1.99_22 or higher
Checking for Apache mod_perl version 1.99_21 or previous
Setup is unable to determine your Apache mod_perl version.
Apache must have module mod_perl enabled. As configuration differs from
mod_perl 1.99_21 or previous AND mod_perl 1.99_22 or higher, Setup must
know which release Apache is using.
You can find which release you are using by running the following command
  - On RPM enabled OS, rpm -q mod_perl
  - On DPKG enabled OS, dpkg -l libapache*-mod-perl*
Enter 1 for mod_perl 1.99_21 or previous.
Enter 2 for mod_perl 1.99_22 and higher.
Which version of Apache mod_perl the computer is running ([1]/2) ?1
OK, Apache is using mod_perl version 1.99_21 or previous ;-)

+----------------------------------------------------------+
|    Checking for Communication server log directory...    |
+----------------------------------------------------------+

Communication server can create detailed logs. This logs can be enabled
by setting integer value of LOGLEVEL to 1 in Administration console
menu Configuration.
Where to put Communication server log directory [/var/log/ocsinventory-server] ?
OK, Communication server will put logs into directory /var/log/ocsinventory-server ;-)

+----------------------------------------------------------------------------+
|    Checking for Communication server plugins configuration directory...    |
+----------------------------------------------------------------------------+

Communication server need a directory for plugins configuration files. 
Where to put Communication server plugins configuration files [/etc/ocsinventory-server/plugins] ?
OK, Communication server will put plugins configuration files into directory /etc/ocsinventory-server/plugins ;-)

+-------------------------------------------------------------------+
|   Checking for Communication server plugins perl directory...     |
+-------------------------------------------------------------------+

Communication server need a directory for plugins Perl modules files.
Where to put Communication server plugins Perl modules files [/etc/ocsinventory-server/perl] ?
OK, Communication server will put plugins Perl modules files into directory /etc/ocsinventory-server/perl ;-)


+----------------------------------------------------------+
| Checking for required Perl Modules...					|
+----------------------------------------------------------+

Checking for DBI PERL module...
Found that PERL module DBI is available.
Checking for Apache::DBI PERL module...
Found that PERL module Apache::DBI is available.
Checking for DBD::mysql PERL module...
Found that PERL module DBD::mysql is available.
Checking for Compress::Zlib PERL module...
Found that PERL module Compress::Zlib is available.
Checking for XML::Simple PERL module...
Found that PERL module XML::Simple is available.
Checking for Net::IP PERL module...
Found that PERL module Net::IP is available.
Checking for Archive::Zip Perl module...
Found that PERL module Archive::Zip is available.


Do you wish to setup Rest API server on this computer ([y]/n)?y

+----------------------------------------------------------+
| Checking for REST API Dependencies ...              		 |
+----------------------------------------------------------+

Found that PERL module Mojolicious::Lite is available.
Found that PERL module Switch is available.
Found that PERL module Plack::Handler is available.

+----------------------------------------------------------+
| Configuring REST API Server files ...               		 |
+----------------------------------------------------------+

Where do you want the API code to be store [/usr/lib64/perl5/vendor_perl] ?
Copying files to /usr/lib64/perl5/vendor_perl

+----------------------------------------------------------+
| Configuring REST API Server configuration files ...  		 |
+----------------------------------------------------------+


+----------------------------------------------------------+
|                 OK, looks good ;-)                       |
|                                                          |
|     Configuring Communication server Perl modules...     |
+----------------------------------------------------------+

Checking if your kit is complete...
Looks good
Generating a Unix-style Makefile
Writing Makefile for Apache::Ocsinventory
Writing MYMETA.yml and MYMETA.json

+----------------------------------------------------------+
|                 OK, looks good ;-)                       |
|                                                          |
|      Preparing Communication server Perl modules...      |
+----------------------------------------------------------+


+----------------------------------------------------------+
|                 OK, prepare finshed ;-)                  |
|                                                          |
|     Installing Communication server Perl modules...      |
+----------------------------------------------------------+


+----------------------------------------------------------+
| OK, Communication server Perl modules install finished;-)|
|                                                          |
|     Creating Communication server log directory...       |
+----------------------------------------------------------+

Creating Communication server log directory /var/log/ocsinventory-server.

Fixing Communication server log directory files permissions.
Configuring logrotate for Communication server.
Removing old communication server logrotate file /etc/logrotate.d/ocsinventory-NG
Writing communication server logrotate to file /etc/logrotate.d/ocsinventory-server


+----------------------------------------------------------------------+
|        OK, Communication server log directory created ;-)            |
|                                                                      |
|   Creating Communication server plugins configuration directory...   |
+----------------------------------------------------------------------+

Creating Communication server plugins configuration directory /etc/ocsinventory-server/plugins.


+----------------------------------------------------------------------+
| OK, Communication server plugins configuration directory created ;-) |
|                                                                      |
|        Creating Communication server plugins Perl directory...       |
+----------------------------------------------------------------------+

Creating Communication server plugins Perl directory /etc/ocsinventory-server/perl.


+----------------------------------------------------------------------+
|     OK, Communication server plugins Perl directory created ;-)      |
|                                                                      |
|               Now configuring Apache web server...                   |
+----------------------------------------------------------------------+

To ensure Apache loads mod_perl before OCS Inventory NG Communication Server,
Setup can name Communication Server Apache configuration file
'z-ocsinventory-server.conf' instead of 'ocsinventory-server.conf'.
Do you allow Setup renaming Communication Server Apache configuration file
to 'z-ocsinventory-server.conf' ([y]/n) ?y
OK, using 'z-ocsinventory-server.conf' as Communication Server Apache configuration file
Removing old communication server configuration to file /etc/httpd/conf.d/ocsinventory.conf
Writing communication server configuration to file /etc/httpd/conf.d/z-ocsinventory-server.conf

+----------------------------------------------------------------------+
|       OK, Communication server setup successfully finished ;-)       |
|                                                                      |
| Please, review /etc/httpd/conf.d/z-ocsinventory-server.conf |
|         to ensure all is good. Then restart Apache daemon.           |
+----------------------------------------------------------------------+


Do you wish to setup Administration Server (Web Administration Console)
on this computer ([y]/n)?y

+----------------------------------------------------------+
|    Checking for Administration Server directories...     |
+----------------------------------------------------------+

CAUTION: Setup now install files in accordance with Filesystem Hierarchy
Standard. So, no file is installed under Apache root document directory
(Refer to Apache configuration files to locate it).
If you're upgrading from OCS Inventory NG Server 1.01 and previous, YOU
MUST REMOVE (or move) directories 'ocsreports' and 'download' from Apache
root document directory.
If you choose to move directory, YOU MUST MOVE 'download' directory to
Administration Server writable/cache directory (by default
/var/lib/ocsinventory-reports), especially if you use deployment feature.

Do you wish to continue ([y]/n)?y
Assuming directories 'ocsreports' and 'download' removed from
Apache root document directory.

Where to copy Administration Server static files for PHP Web Console
[/usr/share/ocsinventory-reports] ?
OK, using directory /usr/share/ocsinventory-reports to install static files ;-)

Where to create writable/cache directories for deployment packages,
administration console logs, IPDiscover and SNMP [/var/lib/ocsinventory-reports] ?
OK, writable/cache directory is /var/lib/ocsinventory-reports ;-)


+----------------------------------------------------------+
|         Checking for required Perl Modules...            |
+----------------------------------------------------------+

Checking for DBI PERL module...
Found that PERL module DBI is available.
Checking for DBD::mysql PERL module...
Found that PERL module DBD::mysql is available.
Checking for XML::Simple PERL module...
Found that PERL module XML::Simple is available.
Checking for Net::IP PERL module...
Found that PERL module Net::IP is available.

+----------------------------------------------------------+
|      Installing files for Administration server...       |
+----------------------------------------------------------+

Creating PHP directory /usr/share/ocsinventory-reports/ocsreports.
Copying PHP files to /usr/share/ocsinventory-reports/ocsreports.
Fixing permissions on directory /usr/share/ocsinventory-reports/ocsreports.
Creating database configuration file /usr/share/ocsinventory-reports/ocsreports/dbconfig.inc.php.
Creating IPDiscover directory /var/lib/ocsinventory-reports/ipd.
Fixing permissions on directory /var/lib/ocsinventory-reports/ipd.
Creating packages directory /var/lib/ocsinventory-reports/download.
Fixing permissions on directory /var/lib/ocsinventory-reports/download.
Creating snmp mibs directory /var/lib/ocsinventory-reports/snmp.
Fixing permissions on directory /var/lib/ocsinventory-reports/snmp.
Creating Administration server log files directory /var/lib/ocsinventory-reports/logs.
Fixing permissions on directory /var/lib/ocsinventory-reports/logs.
Creating Administration server temporary files directory /var/lib/ocsinventory-reports/tmp_dir.
Fixing permissions on directory /var/lib/ocsinventory-reports/tmp_dir.
Creating Administration server scripts log files directory /var/lib/ocsinventory-reports/scripts.
Fixing permissions on directory /var/lib/ocsinventory-reports/scripts.
Configuring IPDISCOVER-UTIL Perl script.
Installing IPDISCOVER-UTIL Perl script.
Fixing permissions on IPDISCOVER-UTIL Perl script.
Writing Administration server configuration to file /etc/httpd/conf.d/ocsinventory-reports.conf

+----------------------------------------------------------------------+
|        OK, Administration server installation finished ;-)           |
|                                                                      |
| Please, review /etc/httpd/conf.d/ocsinventory-reports.conf
|          to ensure all is good and restart Apache daemon.            |
|                                                                      |
| Then, point your browser to http://server//ocsreports
|        to configure database server and create/update schema.        |
+----------------------------------------------------------------------+


Setup has created a log file /home/lab-itop1/ocs/OCSNG_UNIX_SERVER-2.12.3/ocs_server_setup.log. Please, save this file.
If you encounter error while running OCS Inventory NG Management server,
we can ask you to show us its content !

DON'T FORGET TO RESTART APACHE DAEMON !

Enjoy OCS Inventory NG ;-)

[root@LAB-Itop-Jose OCSNG_UNIX_SERVER-2.12.3]#
```

</details>

### configuracion posterior

-  cambiamos las siguientes lineas del /etc/php.ini
```
    post_max_size = 100M
    upload_max_filesize = 100M
```
 - cambiamos el propietario y el htpo de estos directorios
```bash
    sudo chown -R apache:apache /var/lib/ocsinventory-reports
    sudo chown -R apache:apache /usr/share/ocsinventory-reports/ocsreports
    sudo chmod -R 755 /var/lib/ocsinventory-reports
    sudo chmod -R 777 /usr/share/ocsinventory-reports/ocsreports

```

  - le damos todos los permisos necesarios al archivo: /usr/share/ocsinventory-reports/ocsreports/dbconfig.inc.php
```bash
sudo chmod 777 /usr/share/ocsinventory-reports/ocsreports/dbconfig.inc.php

```
- Después de la instalación, por seguridad, vuelve a dejarlo en solo lectura:

```bash
sudo chmod 644 /usr/share/ocsinventory-reports/ocsreports/dbconfig.inc.php

```
### SElinux

```BASH 
sudo setenforce 0

sudo semanage fcontext -a -t httpd_sys_rw_content_t "/usr/share/ocsinventory-reports/ocsreports(/.*)?"
sudo restorecon -Rv /usr/share/ocsinventory-reports/ocsreports

sudo semanage fcontext -a -t httpd_sys_rw_content_t "/var/lib/ocsinventory-reports(/.*)?"
sudo restorecon -Rv /var/lib/ocsinventory-reports

sudo setsebool -P httpd_can_network_connect on


sudo setenforce 1

```

### archivos de configuracion
- /etc/httpd/conf.d/z-ocsinventory-server.conf
```bash 
<Directory "/usr/share/ocsinventory-reports">
	AllowOverride None
	Require all granted
</Directory>

<Directory "/var/www/html/ocsapi">
	Require all granted
</Directory>
```

## Instalacion del AGENTE en linux

- instalacion de dependecias
```bash 
sudo dnf install -y nmap gcc make pciutils dmidecode perl perl-XML-Simple perl-devel perl-Compress-Zlib perl-Digest-MD5 perl-Net-SSLeay

```
- modulos de perl con copan
```bash 
sudo cpan install XML::Simple Compress::Zlib Net::IP LWP::UserAgent Digest::MD5 Net::SSLeay Data::UUID \
IO::Socket::SSL Crypt::SSLeay Proc::Daemon Proc::PID::File Net::SNMP Net::Netmask Nmap::Parser Module::Install \
Net::CUPS Parse::EDID

```
### instalcion de ocs inventory agent

- decomprimir el fichero
```bash
tar -xvzf Ocsinventory-Unix-Agent-2.10.2.tar.gz
```
- compilar el agente
```bash
sudo perl Makefile.PL
sudo make
sudo make install

```

## CONCLUSION