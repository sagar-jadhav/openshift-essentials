# Networking

## Objective
- Access application via Service IP within cluster
- Access application via Service IP outside cluster
- Create route
- Access application via HTTP Route
- Create Edge Terminating Route
- Access application via HTTPS Route 

### Step 1: Deploy nginx application
Refer [User & Project Management](./1_user_and_project_management.md) tutorial

### Step 2: List services
```
oc get svc
```

### Step 3: Access application via service ip within cluster
```
curl http://<SERVICE_IP>:80
```

### Step 4: Access application via service ip outside cluster
```
From browser, Browse http://<SERVICE_IP>:80
```

### Step 5: Create route
```
oc expose service <SERVICE_NAME>
```

### Step 6: Describe route
```
oc get route
```

### Step 7: Access application via HTTP route
```
From browser, Browse http://<ROUTE_URL>
```

### Step 8: Create self-signed certificates
```
openssl genrsa -out example.key 2048
```
```
openssl req -new -key example.key -out example.csr -subj "/C=US/ST=CA/L=Los Angeles/O=Example/OU=IT/CN=test.example.com"
```
```
openssl x509 -req -days 366 -in example.csr -signkey example.key -out example.crt
```

### Step 9: Create edge terminated route
```
oc create route edge --service=nginx --key=example.key --cert=example.crt
```

### Step 6: Describe route
```
oc get route
```

### Step 7: Access application via HTTPS route
``` 
From browser, Browse https://<ROUTE_URL>
```