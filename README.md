Composizione per creare un piccolo ambiente di Hosting (Alpine + Apache + PHP-FPM)
==================================================================================

## Info
Composizione per creare un piccolo ambiente di Hosting (Alpine + Apache + PHP-FPM) che utilizza le seguenti immagini:

- [`scolagreco/docker-mysql`](https://hub.docker.com/r/scolagreco/docker-mysql) verione 5.7.17

- [`scolagreco/alpine_apache_php-fpm`](https://hub.docker.com/r/scolagreco/alpine_apache_php-fpm) verione 7.4

con in più quella standard di Adminer, per poter lavorare sul DB direttamente.

## Configurazione

Nel file *docker-compose.yml* ricordarsi di modificare il valore della variabile d'ambiente *domain* del container *webserver*.

Modificare il file *db_credential.env* :
* *MYSQL_ROOT_PASSWORD* : Password dell'utente ROOT.
* *MYSQL_DATABASE* : Nome del DB.
* *MYSQL_USER* : Nome utente proprietario del DB.
* *MYSQL_PASSWORD* : Password dell'utente proprietario del DB.

Il file *mysqld.cnf* è da cambiare se proprio necessario.

I file *revaliases* e *ssmtp.conf* sono da modificare al bisogno se si ha l'esigenza di inviare mail dal CMS.

Il DB va a finire nella directory "*$PWD/DATA/mysql*", la documentroot (ovvero la */var/www* del container) è invece in "*$PWD/DATA/wwww*".

## Utilizzo

* *git clone https://github.com/scolagreco/hosting-apache.git*
* *cd hosting-apache*
* *docker-compose pull; docker-compose down -v; docker-compose up -d; docker-compose logs -f*

Andare con il browser:

* http://localhost

Per il webserver+php.

* http://localhost:90

Per Adminer. 
