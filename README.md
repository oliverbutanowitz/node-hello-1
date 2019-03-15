# node-hello-1
Simple Node-Hello JS App to use with Openshift S2I

To deploy do:
```
oc new-project myproject
oc new-app https://github.com/oliverbutanowitz/node-hello-1.git
```

To test do (curl http://<service IP>:<Port>/):
```
$ oc get svc
NAME           TYPE        CLUSTER-IP       EXTERNAL-IP   PORT(S)    AGE
node-hello-1   ClusterIP   172.30.123.158   <none>        8080/TCP   13m
$ curl http://172.30.123.158:8080
Hello world - running on node-hello-1-1-jsp2q 
```

You can scale the application:
```
oc scale dc/node-hello-1 --replicas=6
```

And finally watch the LB doing his work (while true;do curl http://<service IP>:<Port>/;sleep 1;done):
```
while true;do curl http://172.30.123.158:8080;sleep 1;done
Hello world - running on node-hello-1-1-jsp2q 
Hello world - running on node-hello-1-1-7nz65 
Hello world - running on node-hello-1-1-rcv4c 
Hello world - running on node-hello-1-1-dn9ct 
Hello world - running on node-hello-1-1-jz98p 
Hello world - running on node-hello-1-1-7nz65 
Hello world - running on node-hello-1-1-jsp2q
```
