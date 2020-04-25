# ocs_inventory_vagrantfile
Vagrantfile to up OCS Inventory in CentOS7

Testado no: CentOS Linux release 7.6.1810 (Core)

Kernel: 3.10.0-957.12.2.el7.x86_64

Sobe o servidor com todas as dependencias, bastando apenas configurar ou desabilitar o firewalld E/OU Selinux.

# Obs:. Isso é uma opção não é recomendado fazer em produção.
## Desabilitar o Selinux:
* sed 's/SELINUX=enforcing/SELINUX=disabled/g' -i /etc/sysconfig/selinux
* sentenforce 0
* systemctl reboot

## Desabilitar o Firewalld
* systemctl stop firewalld.service
* systemctl disable firewalld.service

# Cria banco e da privilegios ao usuario ocs:

* https://mariadb.com/kb/en/mysql_secure_installation/
* mysql_secure_installation

mysql -uroot -p
* MariaDB [(none)]> create database ocsweb;
* MariaDB [(none)]> grant all privileges on ocsweb.* to ocs@localhost identified by "SENHA_QUE_VOCE_QUISER";
* MariaDB [(none)]> flush privileges;
* MariaDB [(none)]> exit

# Acesso HTTP
http://IP_SERVER/ocsreports
