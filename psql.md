## Grundlegdene Elemente ##
im Terminal auf die Postgresdatenbank wechseln.

	sudo -u postgres psql

Mit der Option `\du` werden alle Rollen und Benutzer angezeigt.

##Einstellungen ändern##

	$ cd /etc/postgresql/12/main/

	$ dir
	conf.d       pg_ctl.conf  pg_ident.conf    start.conf
	environment  pg_hba.conf  postgresql.conf

	nano pg_hba.conf
	nano postgresql.conf

	sudo service postgresql restart
	sudo service postgresql status

	sudo reboot -- gesannter Sevrver

## Rollenrechte ##

	-- Rolle read_only
	CREATE ROLE read_only;
	grant connect on database betrieb to read_only;
	grant usage on schema daten, netz, public, vrs, vk_mod_red to read_only;
	grant select on all TABLES in SCHEMA daten, netz, public, vrs, vk_mod_red TO read_only;
	alter DEFAULT privileges in SCHEMA daten, netz, public, vrs, vk_mod_red GRANT SELECT on TABLES TO read_only;
	
	-- rolle read_write
	CREATE ROLE read_write;
	grant connect on database betrieb to read_write;
	grant usage, create on schema daten, netz, public, vrs to read_write;
	grant SELECT, INSERT, UPDATE, DELETE on all TABLES in SCHEMA daten, netz, public, vrs TO read_write;
	alter DEFAULT privileges in SCHEMA daten, netz, public, vrs GRANT SELECT, INSERT, UPDATE, DELETE on TABLES TO read_write;
	GRANT USAGE ON ALL SEQUENCES IN SCHEMA daten, netz, public, vrs TO read_write;
	ALTER DEFAULT PRIVILEGES IN SCHEMA daten, netz, public, vrs GRANT USAGE ON SEQUENCES TO read_write;
	
	-- adler in read_only aktivieren / löschen
	GRANT read_only TO adler;
	drop role adler;

##Verbinungsanziege##

	SELECT
	    max_conn,
	    used,
	    res_for_super,
	    max_conn - used - res_for_super AS res_for_normal
	FROM
	    (
	        SELECT COUNT(*) AS used FROM pg_stat_activity
	    ) t1,
	    (
	        SELECT setting::int AS res_for_super FROM pg_settings WHERE name = 'superuser_reserved_connections'
	    ) t2,
	    (
	        SELECT setting::int AS max_conn FROM pg_settings WHERE name = 'max_connections'
	    ) t3;

Aktivitäten überwachung

	SELECT * FROM pg_stat_activity;

##Links/Quellen##

[https://docs.fedoraproject.org/en-US/quick-docs/postgresql/](https://docs.fedoraproject.org/en-US/quick-docs/postgresql/ "PostgreSQL")

[https://www.atlassian.com/data/admin/how-to-change-a-user-to-superuser-in-postgresql](https://www.atlassian.com/data/admin/how-to-change-a-user-to-superuser-in-postgresql "How to change a user to superuser in PostgreSQL")

[https://www.commandprompt.com/education/how-to-restart-postgresql-server-on-linux/](https://www.commandprompt.com/education/how-to-restart-postgresql-server-on-linux/ "How to Restart PostgreSQL Server on Linux")

[https://stackoverflow.com/questions/61157620/create-extension-postgis-fails](https://stackoverflow.com/questions/61157620/create-extension-postgis-fails "CREATE EXTENSION postgis fails,")

[Benutzerverwatung und -authentifizierung](https://postgresql-buch.de/beispiele:kapitel4 "https://postgresql-buch.de/beispiele:kapitel4")