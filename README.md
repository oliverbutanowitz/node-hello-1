# node-hello-1
Simple Node-Hello JS App to use with Openshift S2I

To deploy do:
```
oc new-project myproject
oc new-app https://github.com/oliverbutanowitz/node-hello-1.git
```

To test do:
```
oc get svc
curl http://<service IP>:<Port>/
```

You can scale the application:
```
oc scale dc/node-hello-1 --replicas=3
```

And finally watch the LB doing his work:
```
while true;do curl http://<service IP>:<Port>/;sleep 1;done
```
