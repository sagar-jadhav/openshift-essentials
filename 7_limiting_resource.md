- Create Quota & Limit Ranges for my-project project

- oc new-project my-project

- oc create quota project-quota --hard=pods=10

- oc describe quota project-quota

- vi limits.yaml

- Add following limits

````
apiVersion: v1
kind: LimitRange
metadata:
    name: project-limits
spec:
    limits:
        -
            type: Container
            max: {cpu: '2'}
            min: {cpu: 100m}
            default: {cpu: 300m}
````

- oc create -f limits.yaml

- oc describe limits project-limits

- oc describe node localhost | grep -A 4 Allocated

- oc new-app -i nodejs:8 https://github.com/sagar-jadhav/node-hello --name nodejs -l app=demo

- oc describe quota project-quota

- oc describe limits project-limits

- oc scale dc nodejs  --replicas=9

- oc describe quota project-quota

- oc describe limits project-limits

- oc scale dc nodejs  --replicas=15

- oc get events
 