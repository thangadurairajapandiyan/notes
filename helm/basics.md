# Helm 2 vs Helm 3
**Reference**
* https://itnext.io/helm2-vs-helm3-part-1-c76c29106e99

**Details**
* Tiller component is removed
* In Helm 2 its two-way strategic merge patch. which means it will compare the old manifest and the proposed chart manifest. In helm3 its three-way strategic merge patch.
It will comapare the old manifest, live state(running in kubernetes cluster, think like manully changes the replica count, which was not known to helm old manifest) and
new proposed chart manifest
