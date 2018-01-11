# Udacity Server
Repo for Udacity server configuration project

IP address: 54.206.47.206
Port: 2200
Url: https://catalog.alexuslab.com/ behing CloudFlare proxy

Software installed:
- mc (midnight commander)
- apache2
- postgresql
- postgresql-contrib
- libapache2-mod-wsgi-py3
- git
- python3-pip
- pip3: flask
- pip3: sqlalchemy
- pip3: google-api-python-client
- pip3: google-auth google-auth-oauthlib google-auth-httplib2
- pip3: psycopg2

Configuration made:
- Package list update
- Updates installed
- Installed required software (see list above)
- /etc/ssh/sshd\_config: port changed to 2200
- ufw: deny all incoming, allow 2200, 80 and 123 tcp ports
- ufw: allow all outgoing
- ufw: enable
- Added "grader" user
- Added him to sudoers via "/etc/sudoers.d/grader" file
- Generated auth key on local machine
- Added key to "/home/grader/.ssh/authorized\_keys"
- Created PostgreSQL user: catalog\_user
- Created PostgreSQL database: catalog
- Made catalog\_user owner of catalog database
- Modified "/etc/apache2/sites-enabled/000-default.conf"
- Added "WSGISriptAlias / /var/www/html/index.wsgi directive"
- Pulled git repo with catalog into /var/www/html folder
- Closed access to .git directory for everyone but owner
- Modified project to use full path for files in file read operations, path is generated relatively to main file in py3
- Create index.wsgi file to make python project compatible with wsgi
- Configured domain 'catalog.alexuslab.com' to point at lightsale server
- Configured CloudFlare crypt service to have https connection instead of http for secure Google Auth

Resources used for reference:
- http://flask.pocoo.org/docs/0.12/deploying/mod_wsgi/
- Stackoverflow
- Udacity videos
