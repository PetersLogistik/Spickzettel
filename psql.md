## Grundlegdene Elemente ##
im Terminal auf die Postgresdatenbank wechseln.

	sudo -u postgres psql

[https://docs.fedoraproject.org/en-US/quick-docs/postgresql/](https://docs.fedoraproject.org/en-US/quick-docs/postgresql/ "PostgreSQL")

[https://www.atlassian.com/data/admin/how-to-change-a-user-to-superuser-in-postgresql](https://www.atlassian.com/data/admin/how-to-change-a-user-to-superuser-in-postgresql "How to change a user to superuser in PostgreSQL")

[https://www.commandprompt.com/education/how-to-restart-postgresql-server-on-linux/](https://www.commandprompt.com/education/how-to-restart-postgresql-server-on-linux/ "How to Restart PostgreSQL Server on Linux")

[https://stackoverflow.com/questions/61157620/create-extension-postgis-fails](https://stackoverflow.com/questions/61157620/create-extension-postgis-fails "CREATE EXTENSION postgis fails,")

## Config Postgres

	$ cd /etc/postgresql/12/main/

	$ dir
	conf.d       pg_ctl.conf  pg_ident.conf    start.conf
	environment  pg_hba.conf  postgresql.conf
	
	nano pg_hba.conf
 	nano postgresql.conf

## Server reboot @Ubuntu

	sudo reboot -- gesannter Sevrver
	sudo service postgresql restart -- nur der Service

## User @Ubuntu
	
	sudo adduser <name>

	sudo userdel <name>

	

