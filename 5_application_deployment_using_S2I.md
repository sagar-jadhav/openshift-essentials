# Application Deployment using Source to Image (S2I)

## Objective
- Deploy Node JS Application using S2I
- Update code
- Rebuild Deployment

### Step 1: Set up Openshift environment
Refer [Getting Started](./get_started.md) tutorial

### Step 2: Login with developer user
```
oc login -u <USER_NAME> -p <USER_PASSWORD> <SERVER_URL>
```

### Step 3: Create project my-project
```
oc new-project my-project
```

### Step 4: Deploy nodejs application using s2i
```
oc new-app -i nodejs:8 https://github.com/sagar-jadhav/node-hello --name nodejs -l app=demo
```

### Step 5: List pods
```
oc get pods --watch
```

### Step 6: List all resources
```
oc get all -l app=demo
```

### Step 7: Create route
```
oc expose service nodejs
```

### Step 8: List route
```
oc get route
```

### Step 9: Browse application
```
From browser, Browse <ROUTE_URL>
```

### Step 10: Clone repository
```
git clone https://github.com/sagar-jadhav/node-hello
```

### Step 11: Update code
```
Update "Hello World !!" string in index.js
```

### Step 12: Rebuild deployment
```
oc start-build nodejs --from-dir=./node-hello/
```
```
oc get pods --watch
```

### Step 13: Browse application
```
From browser, Browse <ROUTE_URL>
```