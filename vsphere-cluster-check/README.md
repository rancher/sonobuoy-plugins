# vSphere Cluster Check

>## _NOTE_
>This plugin is a work in progress. Please file an issue to discuss or request features.
>

The purpose of this plugin is to be able to check that a vSphere cluster using the CPI and CSI charts is working correctly. Currently, only the CPI is being validated with plans to check the deployments and daemonsets are deployed correctly.

## How to use

1. Take the plugin.yaml and modify the input.json data to tweak the versions if different than what you are validating.
2. Download the kubeconfig from your cluster.
3. Run `sonobuoy run -p plugin.yaml`

Example:

```Bash
$ sonobuoy run -p plugin.yaml --wait
time="2022-04-22T09:56:05-04:00" level=info msg="create request issued" name=sonobuoy namespace= resource=namespaces
time="2022-04-22T09:56:05-04:00" level=info msg="create request issued" name=sonobuoy-serviceaccount namespace=sonobuoy resource=serviceaccounts
time="2022-04-22T09:56:05-04:00" level=info msg="create request issued" name=sonobuoy-serviceaccount-sonobuoy namespace= resource=clusterrolebindings
time="2022-04-22T09:56:05-04:00" level=info msg="create request issued" name=sonobuoy-serviceaccount-sonobuoy namespace= resource=clusterroles
time="2022-04-22T09:56:05-04:00" level=info msg="create request issued" name=sonobuoy-config-cm namespace=sonobuoy resource=configmaps
time="2022-04-22T09:56:05-04:00" level=info msg="create request issued" name=sonobuoy-plugins-cm namespace=sonobuoy resource=configmaps
time="2022-04-22T09:56:05-04:00" level=info msg="create request issued" name=sonobuoy namespace=sonobuoy resource=pods
time="2022-04-22T09:56:05-04:00" level=info msg="create request issued" name=plugin-vsphere-cluster-check-cm namespace=sonobuoy resource=configmaps
time="2022-04-22T09:56:05-04:00" level=info msg="create request issued" name=sonobuoy-aggregator namespace=sonobuoy resource=services
09:56:25                   PLUGIN     NODE     STATUS   RESULT           PROGRESS
09:56:25    vsphere-cluster-check   global   complete   passed   2/2 (0 failures)
09:56:25
09:56:25 Sonobuoy has completed. Use `sonobuoy retrieve` to get results.
```

You don't need to modify the other details of the plugin since it's meant to be configuration driven. 

## Future improvements

* CSI deployment check
* CPI daemonset check
* CSI controller and node daemonset checks.