USER & PROJECT MANAGEMENT

- Create a project my-project
- Create 3 Users, project-admin, project-developer
- Assign admin role to project-admin in Project my-project
- Assign developer role to project-developer to Project my-project

1. yum install httpd-tools

2. touch passwordfile 

3. oc projects

4. oc new-project my-project

5. oc create user project-admin

6. htpasswd -b passwordfile project-admin pwd

7. oc create user project-developer

8. htpasswd -b passwordfile project-developer pwd

9. oc policy add-role-to-user admin project-admin

10. oc login -u project-admin -p pwd 2886795315-8443-simba02.environments.katacoda.com

11. oc policy add-role-to-user edit project-developer

12. oc get rolebindings

13. oc login -u project-developer -p pwd 2886795315-8443-simba02.environments.katacoda.com

14. oc new-app --name nginx -l app=demo --docker-image nginx:latest

15. oc get pods

16. oc logs <POD_NAME>

17. oc create sa useroot

18. oc adm policy add-scc-to-user anyuid -z useroot --as system:admin

19. oc get dc

20. oc edit dc nginx

21. Add serviceAccountName: useroot

22. oc get pods --watch

23. oc get pods -o wide

24. curl http://<POD_IP>:80

oc login -u developer -p developer 2886795315-8443-simba02.environments.katacoda.com


