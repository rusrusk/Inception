# The <FROM> instruction initializes a new buil stage and sets the "Base image" for subsequent instructions.
FROM debian:buster

# The <RUN> instruction will execute any commands in a new layer on top of the currebnt image and commit the results.
# The resulting committed image will be used for the next step in Dockerfile
# Installs tools required for project
RUN apt update && apt install -y mariadb-server mariadb-client

#COPY [--chown=<user>:<group>] <src>... <dest>
#The <COPY> instruction copies new files or directories from <src> and adds them to filesystem of the container at the path<dest>
COPY ./conf/my.cnf /etc/mysql/my.cnf
COPY ./tools /var/www/

#<EXPOSE> instruction indicates the ports on which a container listens for conntections.
#We should use traditional port for our application

#<RUN> builds an application 
RUN service mysql start && mysql < /var/www/createdb.sql && rm -f /var/www/createdb.sql

EXPOSE 3306

#<CMD> instruction should be used to run software contained in the image, along with any arguments.
#The main purpose is to provide defaults for an executing container.
CMD /usr/bin/mysqld_safe
