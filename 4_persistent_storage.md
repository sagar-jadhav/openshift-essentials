# Persistent Storage

## Objective
- Deploy **Mongodb** Application
- Create **PersistentVolumeClaim**
- Assign **PersistentVolumeClaim** to **Mongodb** Application
- Verify that data gets stored in Persistent Storage

### Step 1: Set up Openshift environment
Refer [Getting Started](./get_started.md) tutorial

### Step 2: Update environment permissions
```
setenforce 0
```

### Step 3: Deploy mongodb application
```
oc new-app --name mongo -l app=db --docker-image=centos/mongodb-36-centos7 -e MONGODB_ADMIN_PASSWORD=secret
```

### Step 4: List pods
```
oc get pods
```

### Step 5: Describe pod
```
oc describe pod <POD_NAME>
```

### Step 6: Create PersistentVolumeClaim & assign it to mongodb application
```
oc set volume dc/mongo --add --name=<PVC_NAME> -t pvc --claim-size=10Gi  --overwrite --claim-mode="ReadWriteMany"
```
```
Example: oc set volume dc/mongo --add --name=mongo-volume-1 -t pvc --claim-size=10Gi  --overwrite --claim-mode="ReadWriteMany"
```

### Step 7: List PersistentVolumeClaims (PVC's)
```
oc get pvc
```

### Step 8: List PersistentVolumes (PV's)
```
oc get pv
```

### Step 9: Describe pod
```
oc describe pod <POD_NAME>
```

### Step 10: Describe PersistentVolume (PV)
```
oc describe pv <PV_NAME>
```

### Step 11: List files
```
Go to PV location
```
```
ls
```