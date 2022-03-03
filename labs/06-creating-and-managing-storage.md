# Creating and managing pstorage

Storageclaims are the easiest to get some persistent storage to attach to pods wish survives deletion and upgrades of the pod. In this lab you will learn how to:

* Write a Storage claim configuration file
* Attach storage to a pod
* Remove storage

In this lab you will create a Pod named `storage-monolith` and a storage claim called `monolith-storage`. 

## Tutorial: Creating Storage claim

Explore the `monolith-storage` storage configuration file:

```
cat storage/monolith-storage.yaml
```

Create the `monolith-storage` storage using kubectl:

```
kubectl create -f storage/monolith-storage.yaml
```

## Exercise: View Storage details

Use the `kubectl get` and `kubectl describe` commands to view details for the `monolith-storage` PersistentStorageClaim:

### Hints

```
kubectl get pvc
```

```
kubectl describe pvc <StorageClaim>
```

## Tutorial: Mount the storageclaim from a pod

Explore the `storage-monolith` pod configuration file:

```
cat pods/storage-monolith.yaml
```

Create the `storage-monolith` pod using kubectl:

```
kubectl create -f pods/storage-monolith.yaml
```

Ensure that the disk is mounted. 

### Hints

The describe command shows information about volume mount


## Exercise: Touch a file on the volume

Use the `kubectl exec` command to run an interactive shell inside the `monolith` Pod:

```
kubectl exec storage-monolith --stdin --tty -c monolith /bin/sh
df /var/tmp/storage
touch /var/tmp/storage/from_first_instance
ls /var/tmp/storage
```

## Exercise: Remove the pod and recreate it and check if the file still exists

### Hints

The `kubectl delete` command is used to remove a pod, `kubectl delete -f file.yaml` deletes all file defined in file.yaml
