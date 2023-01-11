## Getting started with openshift

## Exploring the openshift webconsole
- OpenShift is often referred to as a container application platform in that it's a platform designed for the development and deployment of applications in [Linux containers](https://developers.redhat.com/topics/containers).
- You use a **project** to group resources in your application. The reason for organizing your application in a **project** is to enable controlled access and quotas for developers or teams.
- You can think of a **project** as a visualization of the Kubernetes namespace based on the developer access controls.
- #note what is a container image? how to make a container image out of a source code?

## Scaling your application
- To scale up application, need to create multiple replicas of the pod that represents the application in the cluster
- Red Hat OpenShift will make it look like all of the replicas are a single application. But, behind the scenes, OpenShift routes traffic among the replicas automatically.
- The benefit of replicating a pod is that it increases the amount of Internet traffic the application can accommodate. The result is better overall performance.
- The word [`pod` is a Kubernetes term](https://kubernetes.io/docs/concepts/workloads/pods/). In this case a `pod` refers to an instance of the application.
- Self Healing ensures that the number of pods you declare for your application are always running.
- After deleting a pod, A replacement pod was created because OpenShift will always make sure that when a pod dies, it creates a new pod to fill its place.

## Routing HTTP Requests
- In Red Hat OpenShift, the **service** resource provides the internal abstraction that binds access to an application to its logic, which is represented in an application's pods. Also, a **service** provides load balancing capabilities within an OpenShift environment.
- The binding of a **service** to an application's pods is internal to an OpenShift cluster. The way that external clients access applications running in OpenShift is through the OpenShift routing layer.
- The formal name for the resource which represents the routing layer is called a **route**.
-  When you create an application from a **container image**, OpenShift creates a **route** for the application automatically.

---
`oc adm policy add-scc-to-user anyuid -z default -n myproject --as system:admin`
