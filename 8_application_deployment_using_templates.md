# Application Deployment using Templates

## Objective
- Create project **my-project**
- Deploy **PHP** Application using Templates

### Step 1: Set up Openshift environment
Refer [Getting Started](./get_started.md) tutorial

### Step 2: Create project my-project
```
oc new-project my-project
```

### Step 3: Update permissions
```
setenforce 0
```

### Step 4: List templates
```
oc get templates -n openshift
```

### Step 5: Describe php template
```
oc describe template cakephp-mysql-persistent -n openshift
```

### Step 6: Deploy php application
```
oc new-app cakephp-mysql-persistent --name cakephp -l app=demo
```
```
oc get pods --watch
```

### Step 7: List route
```
oc get route
```

### Step 8: Access application
```
From browser, Browse http://<ROUTE_URL>
```