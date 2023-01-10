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