
- Deploy Application using Templates


- oc new-project my-project

- setenforce 0

- oc get templates -n openshift

- oc describe template cakephp-mysql-persistent -n openshift

- oc new-app cakephp-mysql-persistent --name cakephp -l app=demo

- oc get pods --watch

- oc get route

- Browse Route_URL