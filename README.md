#### To find how many ReplicaSets exist on the system

```
root@controlplane:~# kubectl get replicaset
NAME              DESIRED   CURRENT   READY   AGE
new-replica-set   4         4         0       70s
```

#### To get how many Pod in the replca set

```
root@controlplane:~# kubectl get rs
NAME              DESIRED   CURRENT   READY   AGE
new-replica-set   4         4         0       2m37s
```

#### To find the image used to create the pods in the new-replica-set

```
root@controlplane:~# kubectl describe replicaset
Name:         new-replica-set
Namespace:    default
Selector:     name=busybox-pod
Labels:       <none>
Annotations:  <none>
Replicas:     4 current / 4 desired
Pods Status:  0 Running / 4 Waiting / 0 Succeeded / 0 Failed
Pod Template:
  Labels:  name=busybox-pod
  Containers:
   busybox-container:
    Image:      busybox777
    Port:       <none>
    Host Port:  <none>
```

#### To see how many PODs are READY in the new-replica-set

```
root@controlplane:~# kubectl get rs
NAME              DESIRED   CURRENT   READY   AGE
new-replica-set   4         4         0   
```
#### To find suitable version for Replicaset

```
kubectl explain replicaset | grep VERSION
VERSION:  apps/v1
```

#### To create a ReplicaSet using the replicaset-definition-1.yaml

```
root@controlplane:~# kubectl create -f replicaset-definition-1.yaml
replicaset.apps/replicaset-1 created
```

#### To delete the replicaset

```
root@controlplane:~# kubectl delete replicaset replicaset-1
replicaset.apps "replicaset-1" deleted
```

#### For editing replcate set

```
root@controlplane:~# kubectl edit replicaset new-replica-set
replicaset.apps/new-replica-set edited
```

#### For scaling replcaset 

```
kubectl edit replicaset new-replica-set
modify the replicas and then save the file

OR

kubectl scale rs new-replica-set --replicas=5 to scale up to 5 PODs.
```
#### For scaling down replicas 

```
root@controlplane:~# kubectl scale rs new-replica-set --replicas=2
replicaset.apps/new-replica-set scaled
```



