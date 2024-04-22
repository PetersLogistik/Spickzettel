# Docker #

## Container ##

Anhalten eines Containers

	docker stop <Containername>

Löschen eines Containers

	docker rm <Containername>

Löscht **alle** Container

	docker container prune 

----------

## Volumes ##
![Filesystem](https://docs.docker.com/storage/images/types-of-mounts-volume.webp?w=450&h=300)

- idr. ist volumes das go-to für die Sicherung von Daten außerhalb der Containerwelt 
- Dateien verbleiben in der Docker-Welt und können direkt nicht eingesehen werden
- Doker verwaltet Volumen selbstständig

Zwei Möglichkeiten für das Erstellen eines Volumes:

1.	Definition vor beginn -> `docker volume create <Name-des-Volumens>`

2.	Erstellung durch den Container. <br>
Hier wird das Volumen bei der Erstnutzung erstellt, wenn es nicht bereits existiert.

Alle erstelleten Volumen einsehen:
	
	docker volume ls
	
	-- für mehr details eine Volumens
	docker volume inspect <Name-des-Volumens>

Zum löschen eines Volumens

	docker volume rm <Name-des-Volumens>

Der Driver kann unterschiedlich gewählt werden. Standart ist local.

Folgende Schreibweisen sind möcglich:

1.	`--mount` in ausführlicher schreibweise
2.	`-v` in kompakter schreibweise 

**--mount**<br>
`type` -> gibt die Halterung an; als [*bind*](https://docs.docker.com/storage/bind-mounts/ "https://docs.docker.com/storage/bind-mounts/"), *volume*, or [*tmpfs*](https://docs.docker.com/storage/tmpfs/ "https://docs.docker.com/storage/tmpfs/") möglich. <br>
`source` -> Standort im Hostsystem; als *source* or *src*. <br>
`destination` -> Wert des Pfad im Container; als *destination*, *dst*, or *target*. <br>
`readonly` -> optional für den "Nur-Lese-Zugriff". <br>
`volume-opt` -> die mehr als einmal angegeben werden kann, nimmt a Schlüsselwertpaar bestehend aus dem Optionsnamen und seinem Wert. <br>

	--Bsp.
	docker service create --mount 'type=volume,src=<VOLUME-NAME>,dst=<CONTAINER-PATH>,volume-driver=local,volume-opt=type=nfs,volume-opt=device=<nfs-server>:<nfs-path>,"volume-opt=o=addr=<nfs-address>,vers=4,soft,timeo=180,bg,tcp,rw"' --name myservice IMAGE

**-v**<br>
Binden eines Volumen an den Container:

	docker run -v <Name-des-Volumens>:/<ordner-stuktur> <container-name>

	-- Bsp. 'hello World'-Container 
	docker run -v MyVolumen:/my_file hello-world
Hier wird ein Container Erstellt das Volumen heißt `MyVolumen` und wird im Ordnerpfad `/my_file` dem Container mitgegeben. `hello-world` ist das Container-Image. <br>
Alles was in dem Ordner `my_file` erstellt wird, kann bei restart des Containers wieder abgerufen werden. Auch bei löschung der Container "überlebt" die Volumendatei. 

Löschen eines Volumens
	
	docker volume rm <Volumenname>

## Bind Mount ##

- können über den Pfad im Host-System eingesehen werden (im Explorer sichtbar)
- einfach den Pfad im Container angeben
- nicht für Produktive "Sachen" geeignet. -> eher Volumes nutzen

Syntax

	docker run -v <Verzeichnispfad>:<pfad-im-Container> <Comadline-Image-Befehle>
	
	--Bsp. statische Webseite
	docker run -p 8000:80 -v /Users/Sorce/quadroid:/mydata:ro -d nginx

Die Zeile erstellt eine nginx Webseite. Dazu zieht er sich alle Dateien aus dem Pfad: `/Users/Sorce/quadroid` in die Containerstruktur `/mydata`. Das `:ro` steht für *read only*. Andere Befehle wie 
Das `-p 8000:80` steht für den Portzugang der Webseite im Docker.

## Links / Quellen:  ##
[docker.docs - Volumes](https://docs.docker.com/storage/volumes/ "https://docs.docker.com/storage/volumes/") <br>
[Docker Volumes: Efficient Data Management in Containerized Environments](https://semaphoreci.com/blog/docker-volumes "https://semaphoreci.com/blog/docker-volumes") <br>
[Docker - Persistente Daten mit Volumes und Bind Mount - youTube](https://www.youtube.com/watch?v=PdVM7WVnWXc "https://www.youtube.com/watch?v=PdVM7WVnWXc") <br>
[docker.docs - Bind mounts](https://docs.docker.com/storage/bind-mounts/ "https://docs.docker.com/storage/bind-mounts/")

----------
