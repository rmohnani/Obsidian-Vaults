https://developers.redhat.com/learn/log-into-openshift-cluster

## Logging in via the web console
- command to check pod responsible for openshift web console is available: `oc get pods -n openshift-console | grep console`. Should get: `console-7d599cbf78-4xc9v 1/1 Running 0 23mD`
- command to find route to web console: `oc get routes console -n openshift-console -o jsonpath='{"https://"}{.spec.host}{"\n"}'`. Example url output: `oc get routes console -n openshift-console -o jsonpath='{"https://"}{.spec.host}{"\n"}'`
- 