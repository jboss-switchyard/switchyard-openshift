SwitchYard on OpenShift Express
===============================

This template helps you get up and running quickly with a SwitchYard application on
OpenShift Express.

Create an account at http://openshift.redhat.com/

Create a jbossas-7.0 application

    rhc-create-app -a swydapp -t jbossas-7.0

Add this upstream SwitchYard repo

    cd swydapp
    git remote add upstream -m master git://github.com/mageshbk/openshift-express.git
    git pull -s recursive -X theirs upstream master
    git apply standalone.diff
    git add .
    git commit -m 'Added SwitchYard subsystem'

Then push the repo to origin

    git push

That's it, you can now checkout your application at:

    http://swydapp-$yourdomain.rhcloud.com

This repository will deploy a sample called osdemo.jar binary deployment. You can
checkout the SOAP WSDL of this sample at

    http://swydapp-$yourdomain.rhcloud.com/swydws/ProcessOrder?wsdl

This repository is also a barebone SwitchYard application for source development.
Read more at the cloud link posted above of your application on how to build and
deploy a new SwitchYard application from scratch.

Remember to enable openshift profile, if you update the source files, by renaming
the pom.xml's profile from 
    <id>switchyard</id>
to
    <id>openshift</id>
