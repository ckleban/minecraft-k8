# minecraft-k8


#Create pod
> kubectl create -f pod.yml

#See it up and running:
> kubectl get pods
NAME                      READY     STATUS    RESTARTS   AGE
minecraft-dfhse           1/1       Running   0          2h

#If you want this server to be reachable on the internet, you probably need to do some more things. If you are on a public cloud, like Centurylink, amazon or google, this is easy to do. Simply run:

> kubectl expose pod minecraft-server --port=25565 --type=LoadBalancer

You will be given a public IP address, which you can see by running:

> kubectl get services


-------------------------------------


That is it. You and your friends can now play minecraft, inside docker, on kubernetes. 

A few things to note:
you may need to wait a few minutes while you wait for the external IP address to be published. 
you may also need to open up a firewall rule to this IP address and port. 
this isn't a durable configuration. If the pod dies, it won't come back online and the save games and world will be gone for ever. These problems are easily solved in kubernetes. We just need to add a replication controller and persistent storage. Perhaps, I'll work on that next and post it sometime. 
