Persistent Storage

- Deploy MongoDB App
- Retrieve available PV's
- Create PVC
- Associate PVC to DC
- Verify that data get stored in PV
- Change the file
- Browse the application

- getenforce

- setenforce 0

- oc new-app --name mongo -l app=db --docker-image=centos/mongodb-36-centos7 -e MONGODB_ADMIN_PASSWORD=secret

- oc get pods

- oc describe pod <POD_NAME>

4. oc set volume dc/mongo --add --name=<PVC_NAME> -t pvc --claim-size=10Gi  --overwrite

e.g oc set volume dc/mongo --add --name=mongo-volume-1 -t pvc --claim-size=10Gi  --overwrite --claim-mode="ReadWriteMany"

5. oc get pvc

6. oc get pv --system:admin

7. oc describe pod <POD_NAME>

8. oc describe pv <PV_NAME> --as system:admin

9. Go to PV location

10. ls
