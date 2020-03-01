# Scaling an Application

## Objective
- Scale up nginx application using **oc scale** command
- Scale up nginx application by updating **DeploymentConfig**
- Scale down nginx application using **oc scale** command

### Step 1: Deploy nginx application
Refer [User & Project Management](./1_user_and_project_management.md) tutorial

### Step 2: List pods
```
oc get pods
```

### Step 3: Scale up nginx application using oc scale command
```
oc scale dc nginx --replicas=5
```
```
oc get pods --watch
```

### Step 4: Scale up nginx application by updating DeploymentConfig
```
oc edit dc nginx
```
```
update replicas = 7
```
```
oc get pods --watch
```

### Step 5: Scale down nginx application using oc scale command
```
oc scale dc nginx --replicas=1
```
```
oc get pods --watch
```