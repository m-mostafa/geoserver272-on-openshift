A quickstart for GeoServer to run on OpenShift

CREDIT: https://www.openshift.com/blogs/build-your-own-google-maps-and-more-with-geoserver-on-openshift

		http://blog.geopaas.io/?page_id=100

This was tested on openshift's Tomcat 7 (JBoss EWS 2.0)

The GeoServer is a version 2.7.2 WAR file.

Also please read the [blog post](https://www.openshift.com/blogs/build-your-own-google-maps-and-more-with-geoserver-on-openshift) for further detials.


=============================

Here are the instructions to add this git repo to a blank tomcat 7 application (on openShift) 
At the windows command prompt navigate to a suitable folder (where you clone the application files), then enter the commands as follows:

	rhc app create geoserver -s tomcat7 postgresql-9

    cd geoserver

	git remote add github -m master https://github.com/m-mostafa/geoserver272-on-openshift.git

	git pull -s recursive -X theirs github master
	
	git rm pom.xml
	
	git commit -am "initial commit"

	git push origin
	

Finally set CATALINA_OPTS

	rhc set-env --env CATALINA_OPTS=/var/lib/geoserver-{your domain}.rhcloud.com/app-root/data/geoserver_data --app geoserver	
	
Once it works, the URL to access it will be:

http://geoserver-{your domain}.rhcloud.com/web


