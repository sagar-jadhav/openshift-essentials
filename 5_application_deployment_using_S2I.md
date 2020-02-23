Application deployment using S2I

- Deploy Node JS Application using S2I
- Update code
- Restart deployment

- oc login -u <DEVELOPER> -p <DEVELOPER> <URL>

- oc new-project my-project

- oc new-app -i nodejs:8 https://github.com/sagar-jadhav/node-hello --name nodejs -l app=demo

- oc get pods --watch

- oc get all -l app=demo

- oc expose service nodejs

- oc get route

- Browse <Route_URL>

- git clone https://github.com/sagar-jadhav/node-hello

- Update index.js

- oc start-build nodejs --from-dir=./node-hello/

- oc get pods --watch

- Browse <Route_URL>