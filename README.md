PyroCMS on OpenShift
====================

This git repository helps you get up and running quickly w/ a PyroCMS installation
on OpenShift.  The backend database is MySQL and the database name is the 
same as your application name (using $_ENV['OPENSHIFT_APP_NAME']).  You can call
your application by whatever name you want (the name of the database will always
match the application).


Running on OpenShift
----------------------------

Create an account at http://openshift.redhat.com/

Create a php-5.3 application (you can call your application whatever you want)

    rhc app create -a pyrocms -t php-5.3

Add MySQL support to your application

    rhc app cartridge add -a pyrocms -c mysql-5.1

Add this upstream pyrocms repo

    cd pyrocms
    git remote add upstream -m master git://github.com/Atriedes/openshift-pyrocms.git
    git pull -s recursive -X theirs upstream master
    # note that the git pull above can be used later to pull updates to PyroCMSs
    
Then push the repo upstream

    git push

That's it, you can now checkout your application at (default admin account is admin/admin):

    http://pyrocms-$yournamespace.rhcloud.com
    http://pyrocms-$yournamespace.rhcloud.com/admin for PyroCMS Administration

