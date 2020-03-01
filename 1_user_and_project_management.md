# User & Project Management

## Objective
- Create project **my-project**
- Create 2 Users **project-admin** & **project-developer**
- Assign admin role to user project-admin in project my-project
- Assign developer role to user project-developer in project my-project

### Step 1: Set up Openshift environment
Refer [Getting Started](./get_started.md) tutorial

### Step 2: Set up utility
Install httpd tools
```
yum install httpd-tools
```
Create file to store user & password
```
touch passwordfile 
```

### Step 3: List projects
```
oc projects
```
### Step 4: Create project
```
oc new-project my-project
```

### Step 5: Create users
```
oc create user project-admin
```
```
htpasswd -b passwordfile project-admin pwd
```
```
oc create user project-developer
```
```
htpasswd -b passwordfile project-developer pwd
```

### Step 6: Add admin role to user
```
oc policy add-role-to-user admin project-admin
```

### Step 7: Add developer role to user
```
oc login -u project-admin -p pwd <SERVER_URL>
```
```
oc policy add-role-to-user edit project-developer
```

### Step 8: List role bindings
```
oc get rolebindings
```

### Step 9: Deploy application 
```
oc login -u project-developer -p pwd <SERVER_URL>
```
```
oc new-app --name nginx -l app=demo --docker-image nginx:latest
```

### Step 10: List pods
```
oc get pods
```

### Step 11: View application logs
```
oc logs <POD_NAME>
```

### Step 12: Create service account
```
oc create sa useroot
```

### Step 13: Add scc anyuid to service account
```
 oc adm policy add-scc-to-user anyuid -z useroot --as system:admin
```

### Step 14: Patch DC with service account
```
 oc get dc
```
```
oc patch dc/nginx --patch \
'{"spec":{"template":{"spec":{"serviceAccountName": "useroot"}}}}'
```
```
oc get pods --watch
```

### Step 15: Browse application
```
oc get pods -o wide
```
```
curl http://<POD_IP>:80
```



