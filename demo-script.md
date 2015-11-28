#####################
# Prep
#####################

oc new-project myproject
oc policy add-role-to-user view system:serviceaccount:$(oc project -q):default -n $(oc project -q)
printf "127.0.0.1\tmyapp-myproject.apps.example.com" | sudo tee -a /etc/hosts


#####################
# Simple Cluster
#####################
1. Use the datagrid65-basic template to create an jdg-cluster with the following parameters
  - NAME: myapp
  - CACHE_NAMES: mycluster
  - MEMCACHE_CACHE: mycache
2. When created scale the cluster to 4 nodes
3. Show log files that the pods will join the cluster
4. Show the topology of the cluster

#####################
# REST
#####################
1. Go to the overview of the cluster
2. Explain that the rest service is routed
3. Use curl to enter some data into the cluster

```
for key in {1..100}
do
  curl -X PUT -d "DATA for key $key
" http://myapp-myproject.apps.example.com/rest/mycache/$key
done
```
        curl http://myapp-myproject.apps.example.com/rest/mycache/56

4. Show the topology of the cluster
5. Connect to the terminal in one of the nodes
6. Start the CLI
        $ /opt/datagrid/bin/cli.sh -c
        # cache mycache
        # stats
        # locate 30
        # locate 55
        # locate 98
        # get "34"

  In another console window

        $ echo "REFUQSBmb3Iga2V5IDM0Cg==" | base64 -D

7. Delete the content of myproject

        $ oc delete all --all

###################
# Persistance
###################
