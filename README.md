# Ansible Role: Backup MySQL database to AWS S3 via Docker container

An Ansible role to backup MySQL databases to AWS S3 via a Docker container. This role uses the [iainmckay/mysql-backup](https://hub.docker.com/r/iainmckay/mysql-backup/) docker container.

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

To backup 1 or several databases, add the database names to the `command` variable: `backup db1 db2 ...`.

A value of `backup` for the `command` variable should backup all databases. However, at the time of this writing, a bug in the `iainmckay/mysql-backup` container causes an error.

## Example playbook

```
---
- hosts: mysql_server
  roles:
  	- opichon.mysql-backup
  	  command: backup <db1> <db2>
```

## License

MIT

