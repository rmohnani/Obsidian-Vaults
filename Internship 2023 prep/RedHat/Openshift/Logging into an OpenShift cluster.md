https://developers.redhat.com/learn/log-into-openshift-cluster

## Logging in via the web console
- command to check pod responsible for openshift web console is available: `oc get pods -n openshift-console | grep console`. Should get: `console-7d599cbf78-4xc9v 1/1 Running 0 23mD`
- command to find route to web console: `oc get routes console -n openshift-console -o jsonpath='{"https://"}{.spec.host}{"\n"}'`. Example url output: `oc get routes console -n openshift-console -o jsonpath='{"https://"}{.spec.host}{"\n"}'`

## Logging in via the command line
- command to log into openshift. `-u` specifies username and `-p` specifies password. 
- command to enter project namespace `oc project {project_name}`
- command to see all projects `oc get projects`
- command to verify user `oc whoami`. `--show-server` flag to verify server

## Collaborating with other users
- command to create new user with username and password: user1. `oc login --username user1 --password user1`
- for `oc get projects` we get no resources found. 
- command to create a new project `oc new-project {project_name}`. 
- command to add assign view permissions to user developer: `oc adm policy add-role-to-user view developer -n yourproject`

## Switching users between accounts
- If I had an account for  [Developer Sandbox for OpenShift](https://developers.redhat.com/developer-sandbox) , I could write: `oc login --token=<token> --server=https://api.sandbox-m2.ll9k.p1.openshiftapps.com:6443`. 
- When switching between OpenShift clusters, if you do not explicitly say which user to use, OpenShift will use the last user logged into the cluster. You can still provide `--username` if required.
- Switching among users without needing to supply the password or register with a token is possible because the details for each user are saved separately in what is called a context.
- command to show current context: `oc whoami --show-context`
- command to list all clusters logged into: `oc config get-clusters`
- command to list all contexts ever created: `oc config get-contexts`
- 