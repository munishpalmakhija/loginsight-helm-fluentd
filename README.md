# loginsight-helm-fluentd

This repo contains helm charts to push Kubernetes Logs to vRealize Log Insight using fluentd daemonset. 

# Pre-requisities 

You need to have following pre-requisties 

1.	vRealize LogInsight FQDN/IP
2.	Helm Version = '3.x'
3.  Admin access to the Kubernetes Cluster

# Installing the Chart - Procedure 1 

## Add Chart Repo 
```
helm repo add loginsight https://munishpalmakhija.github.io/loginsight-helm-fluentd/
```


## Get Values file in your working directory 
```
helm show values loginsight/loginsight-helm-fluentd  > values.yaml
```

## Update Values file with API Token and other relevant details.  
```
cat values.yaml
```

## Install Chart.  
```
helm install vrli-fluentd-helm-test loginsight/loginsight-helm-fluentd -f values.yaml
```

## Verify Kubernetes Pods  
```
kubectl get pods -A | grep vrli-fluentd-helm-test
```

## Verify Helm Release 
```
helm list
```

# Installing the Chart - Procedure 2

## Add Chart Repo 
```
helm repo add loginsight https://munishpalmakhija.github.io/loginsight-helm-fluentd/
```


## Install Chart by setting values during run time.  

```
helm install vrli-fluentd-helm-test loginsight/loginsight-helm-fluentd --set vrli.host=SETME --set tag.environment=DEMO
```

## Verify Kubernetes Pods  
```
kubectl get pods -A | grep vrli-fluentd-helm-test
```
## Verify Helm Release 
```
helm list
```