SCALING AN Application

- Scale up application using oc scale command
- Scale up bt updating DC
- Scale down

1. oc get pods

2. oc scale dc nginx --replicas=5

3. oc get pods --watch

4. oc edit dc nginx

update replicas = 7

5. oc get pods --watch

6. oc scale dc nginx --replicas=1