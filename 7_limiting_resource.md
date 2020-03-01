# Limiting Resources

## Objective
- Create project **my-project**
- Create Quota & Limit Ranges for project **my-project**
- Deploy Node JS Application using S2I
- Verify allocated Quota & Limits

### Step 1: Set up Openshift environment
Refer [Getting Started](./get_started.md) tutorial

### Step 2: Create project my-project
```
oc new-project my-project
```

### Step 3: Create quota
```
oc create quota project-quota --hard=pods=10
```

### Step 4: Describe quota
```
oc describe quota project-quota
```

### Step 5: Create limit ranges
```
vi limits.yaml
```
Add following limit range

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
```
oc create -f limits.yaml
```

### Step 6: Describe limit ranges
```
oc describe limits project-limits
```

### Step 7: Describe node
```
oc describe node localhost | grep -A 4 Allocated
```

### Step 8: Deploy nodejs application using s2i
- oc new-app -i nodejs:8 https://github.com/sagar-jadhav/node-hello --name nodejs -l app=demo

### Step 9: Describe quota
```
oc describe quota project-quota
```

### Step 10: Describe limit
```
oc describe limits project-limits
```

### Step 11: Scale up nodejs application
```
oc scale dc nodejs --replicas=9
```

### Step 12: Describe quota
```
oc describe quota project-quota
```

### Step 13: Describe limit
```
oc describe limits project-limits
```

### Step 14: Scale up nodejs application
```
oc scale dc nodejs --replicas=15
```

### Step 15: List pods
```
oc get pods
```

### Step 16: List events
```
oc get events
``` 