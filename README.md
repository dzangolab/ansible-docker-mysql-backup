# Ansible Role: Backup MySQL databases to AWS S3 via Docker container

An Ansible role to backup MySQL databases to AWS S3 via a Docker container. This role uses the [iainmckay/mysql-backup](https://hub.docker.com/r/iainmckay/mysql-backup/) docker image.

## Requirements

This role requires Ansible 1.2 or higher.

It also requires the Docker engine to run on the target host.

## Role variables

Ansible variables are listed below with their default values.

```
mysql_backup_command: backup
mysql_backup_aws_access_key_id
mysql_backup_aws_secret_access_key
mysql_backup_aws_region
mysql_backup_host
mysql_backup_user
mysql_backup_password
mysql_backup_s3_bucket
mysql_backup_s3_path
```

For the significance of these variables, see the documentation of the [iainmckay/mysql-backup](https://hub.docker.com/r/iainmckay/mysql-backup/) docker image.

## Example playbooks

```
---
- 	hosts: mysql_server
	roles:
		- name: Backup db1 and db2 databases
		  role: opichon.mysql-backup
		  mysql_backup_command: backup db1 db2
```

```
---
- 	hosts: mysql_server
	roles:
		- name: Restore db1 and db2 databases
		  role: opichon.mysql-backup
		  mysql_backup_command: restore db1 db2
```

## License

MIT

