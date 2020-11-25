# Helm 2 vs Helm 3

**Details**
* Tiller component is removed
* In Helm 2 its two-way strategic merge patch. which means it will compare the old manifest and the proposed chart manifest. In helm3 its three-way strategic merge patch.
It will comapare the old manifest, live state(running in kubernetes cluster, think like manully changes the replica count, which was not known to helm old manifest) and
new proposed chart manifest
* For helm upgrade, in helm 3 it forces the resources in chart, lets say you deployed a pod with one app container(version 1.0.0) using helm, now you manualy installed istio service-mesh, which will attach one more side-car container to our pod, so our pod will now have 2 containers. If we upgrade the app container version to 1.1.0 using helm2,
it will check the old manifest and new manifest and it will remove that side-car container, since it doest exist in old manifest and update the app container version. Using Helm 3, it will compare the old maifest, live state and new manifest, now it knows, we have one more side-car container and will just update ony the app container version and still the side-car container will be running
* 

**Reference**
* https://itnext.io/helm2-vs-helm3-part-1-c76c29106e99
