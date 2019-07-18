# Ansible Role: Backup MySQL databases to AWS S3 via Docker container

An Ansible role to backup MySQL databases to AWS S3 via a Docker container. This role uses the [iainmckay/mysql-backup](https://hub.docker.com/r/iainmckay/mysql-backup/) docker image.

See also [dzangolab.docker_mysql](https://galaxy.ansible.com/dzangolab/docker_mysql/)

## Requirements

This role requires Ansible 1.2 or higher.

It also requires the Docker engine to run on the target host.

## Role variables

Ansible variables are listed below with their default values.

```
mysql_backup_databases: "--all-databases"
mysql_backup_dump_options: "--quote-names --quick --add-drop-table --add-locks --allow-keywords --disable-keys --extended-insert --single-transaction --create-options --comments --net_buffer_length=16384"
mysql_backup_host: mysql
mysql_backup_multifiles: true
mysql_backup_port: 3306
mysql_backUP_s3_region: "eu-west-1"
mysql_backup_schedule: "@daily"

mysql_backup_password
mysql_backup_user
mysql_backup_s3_access_key_id
mysql_backup_s3_bucket
mysql_backup_s3_prefix
mysql_backup_s3_secret_access_key
```

For the meaning of these variables, see the documentation of the [schickling/mysql-backup-s3](https://github.com/schickling/dockerfiles/tree/master/mysql-backup-s3) docker image.

## Example playbooks

```
---
- 	hosts: mysql_server
	roles:
		- name: Backup db1 and db2 databases
		  role: dzangolab.mysql_backup
		  mysql_backup_command: backup db1 db2
```

```
---
- 	hosts: mysql_server
	roles:
		- name: Restore db1 and db2 databases
		  role: dzangolab.mysql-backup
		  mysql_backup_command: restore db1 db2
```

## License

MIT

