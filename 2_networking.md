NETWORKING

- Access application via Service within cluster
- Access application via Service IP outside cluster
- Create route
- Access application via http Route
- Create Edge Terminates Route
- Access application via https Route 

1. oc get svc

2. curl http://<SERVICE_IP>:80

3. Browse with http://<SERVICE_IP>:80

4. oc expose service <SERVICE_NAME>

5. oc get route

6. Browse http://<ROUTE_URL>

Creating certs

7. openssl genrsa -out example.key 2048

8. openssl req -new -key example.key -out example.csr -subj "/C=US/ST=CA/L=Los Angeles/O=Example/OU=IT/CN=test.example.com"

9. openssl x509 -req -days 366 -in example.csr -signkey example.key -out example.crt

10. oc create route edge --service=nginx --key=example.key --cert=example.crt

11. oc get route

12. Browse https://<ROUTE_URL>
