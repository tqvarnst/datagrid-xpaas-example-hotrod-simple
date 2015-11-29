JBoss DataGrid Examples on OpenShift
=========================

This repo contains various example on how to use the xPaaS images for JBoss Data Grid on OpenShift.

Currently these images are not released and therefor the current branch 1.2 is using an internal.

Running on OpenShift
--------------------

You need to have access to OpenShift Enterprise (OSE) v3.1 and a OpenShift Command Line Interface (CLI) tools installed. You can download the latest OSE CLI here: https://github.com/openshift/origin/releases

To install the image stream and temlpate on openshift project you need access rights to the openshift project. This can be can be accomplished by using the the following command (where "demo" that should be given edit access to the openshift project)

        $ oc policy add-role-to-user edit demo -n openshift

Login to your openshift instance

        oc login <url to your OSE environment> -u demo

for example

        oc login openshift.example.com -u demo

Create the image stream and the project

        oc create -f jboss-datagrid-image-stream.json -n openshift
        curl https://raw.githubusercontent.com/jboss-openshift/application-templates/master/datagrid/datagrid65-basic.json | oc create -n openshift -f -

Run the demo     
-----------
Please see the [demo-script.md] for more details
