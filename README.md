SwitchYard on OpenShift Express
===============================

This template helps you get up and running quickly with a SwitchYard application on
OpenShift Express.

Create an account at http://openshift.redhat.com/

Create a jbossas-7 application

    rhc-create-app -a swydapp -t jbossas-7

Add this upstream SwitchYard repo

    cd swydapp
    git remote add upstream -m master git://github.com/jboss-switchyard/switchyard-openshift.git
    git pull -s recursive -X theirs upstream master
    git apply standalone.diff
    git add .
    git commit -m 'Added SwitchYard subsystem'

Then push the repo to origin

    git push

That's it, you can now checkout your application at:

    http://swydapp-$yourdomain.rhcloud.com

Samples deployed with your application
--------------------------------------

This repository will deploy a sample called osdemo.jar binary deployment. You can
checkout the SOAP WSDL of this sample at

    http://swydapp-$yourdomain.rhcloud.com/swydws/OrderService?wsdl

You can test this application using your favourite SOAP client. A valid SOAP request
is shown here:

    <soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/"
       xmlns:urn="urn:switchyard-quickstart:bean-service:1.0">
       <soapenv:Header/>
       <soapenv:Body>
          <urn:submitOrder>
             <order>
                <orderId>1</orderId>
                <itemId>BUTTER</itemId>
                <quantity>20</quantity>
             </order>
          </urn:submitOrder>
       </soapenv:Body>
    </soapenv:Envelope>

Source development
------------------

This repository is also a barebone SwitchYard application for source development.
Read more at the cloud link of your application from here, once it is deployed.

    http://swydapp-$yourdomain.rhcloud.com

Remember to enable openshift profile, if you update the source files, by renaming
the pom.xml's profile from

    <id>switchyard</id>

to

    <id>openshift</id>
