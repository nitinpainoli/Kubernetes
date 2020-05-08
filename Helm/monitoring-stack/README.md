# Introduction
This chart deploy all the deployments on a Kubernetes cluster/Minikube using the Helm package manager.


## Application Installed
The following packages will be installed by this helm chart
* Grafana
* Prometheus
* Alert-manager


## Prerequisite
* Kubernetes or Minikube installed
* Helm

## Installing the Chart

If you need to update the variable values you can change in the values.yaml file in the helm chart

To install the chart run the below command in the home of the  project. make sure you have helm installed in your minikube/kubernetes cluster

```sh
$ helm install . --generate-name
```
Confirm the deployment by, running the command:

```sh
$ helm status name_of_the_release
```

## Uninstalling the Chart

To uninstall/delete the all the deployments

```sh
$ helm delete name_of_the_release
```

### To acccess the service

 ```sh
 $ kubectl get svc
 ```

```
NAME                                             TYPE        CLUSTER-IP       EXTERNAL-IP   PORT(S)          AGE
chart-1588915585-monitoring-stack-alertmanager   NodePort    10.104.205.104   <none>        9093:31495/TCP   4m1s
chart-1588915585-monitoring-stack-grafana        NodePort    10.103.244.191   <none>        3000:30999/TCP   4m1s
chart-1588915585-monitoring-stack-prometheus     NodePort    10.97.179.210    <none>        9090:30990/TCP   4m1s


```

To access grafana type NodeIP:port-no ( e.g nodeip:31188)

To access prometheus type NodeIP:port-no ( e.g nodeip:30718)

To access alertmanager type NodeIP:port-no

## Configuration

The following table lists the configurable parameters for this helm chart and their default values set.


### Grafana
| Parameter	  | Description | Default |
| ------      | ------      | ------ |             
| replicaCount | replica for your deployment | 1 |
| grafana.image.repository |image repository for grafana  | `grafana/grafana:latest` |
| grafana.GfSecurityAdminUser | GfSecurityAdminUser for grafana | admin |
| grafana.GfSecurityAdminPassword | GfSecurityAdminPassword for grafana | admin |
| grafana.GfAuthAnonymousEnabled| GfAuthAnonymousEnabled for grafana | true |
| grafana.GfAuthAnonymousOrgRole| GfAuthAnonymousOrgRole for grafana | Admin|
| grafana.service.type | service type for grafana | `NodePort` |
| grafana.service.port | Port no. for grafana  | `3000` |

### Prometheus
| Parameter	  | Description | Default |
| ------      | ------      | ------ |
| replicaCount | replica for your deployment | 1 |
| prometheus.image.repository |image repository for prometheus  | `prom/prometheus:v2.10.0` |
| prometheus.service.type | service type for prometheus | `NodePort` |
| prometheus.service.port | Port no. for prometheus | `9090` |

## Alertmanager
| Parameter	  | Description | Default |
| ------      | ------      | ------ |
| replicaCount | replica for your deployment | 1 |
| alertmanager.image.repository | image repository for alertmanager | `prom/alertmanager:latest` |
| alertmanager.service.port | Port no. for alertmanager | `9093` |
| alertmanager.service.type | service type for alertmanager | `NodePort` |
