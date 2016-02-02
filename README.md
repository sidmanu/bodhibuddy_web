# bodhibuddy
Django website to act as an assistant for SGI members.

How to setup Virtual Host on Ubuntu:

The project is kept under /home/ubuntu/bodhibuddy.in folder. 


The contents of /etc/apache2/sites-enabled/bodhibuddy.in.conf is:

$ cat bodhibuddy.in.conf
<VirtualHost *:80>

    ServerName www.bodhibuddy.in
    ServerAlias bodhibuddy.in
    ServerAdmin webmaster@bodhibuddy.in

    DocumentRoot /home/ubuntu/bodhibuddy.in/planner

	Alias /static/ /home/ubuntu/bodhibuddy.in/planner/static/

	<Directory /home/ubuntu/bodhibuddy.in/planner/static/*>
	    Require all granted
	</Directory>
	WSGIDaemonProcess bodhibuddy python-path=/home/ubuntu/bodhibuddy.in/planner
    	WSGIProcessGroup bodhibuddy

	WSGIScriptAlias / /home/ubuntu/bodhibuddy.in/planner/planner/wsgi.py
	<Directory /home/ubuntu/bodhibuddy.in/planner>
	    <Files wsgi.py>
		Order deny,allow
		Require all granted
	    </Files>
	</Directory>


</VirtualHost>
