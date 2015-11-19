Hot Rod Simple - JBoss DataGrid Example on OpenShift
=========================

This example project shows how to use JBoss Data Grid as a data storage using Hot Rod on OpenShift Enterprise V3.x

Running on OpenShift
--------------------

You need to have access to OpenShift Enterprise (OSE) v3.0 and a OpenShift Command Line Interface (CLI) tools installed. You can download the latest OSE CLI here: https://github.com/openshift/origin/releases

Login to your openshift instance

    oc login <url to your OSE environment>

for example

    oc login openshift.example.com

Create a new project (if it doesn't already exist)

    oc new-project datagrid-examples

Create the image stream and the project

    oc create -f jboss-datagrid-image-stream.json
    oc create -f jboss-datagrid-template-simple-hotrod.json

Create the application based on the template

    oc new-app jdg-simple-hotrod-example

Clean up
-----------
To clean up the project when you are don run the following command

    oc delete all --all
