# ☸️ SECTION 5: Storage in Kubernetes

### What is Persistent Volume (PV)?
> A Persistent Volume is a cluster-level storage resource in Kubernetes.
> It represents actual physical storage like NFS, AWS EBS, Azure Disk, etc., provisioned by an administrator or dynamically.

### What is Persistent Volume Claim (PVC)?
> A Persistent Volume Claim is a request for storage by a Pod.
> It defines required storage size and access mode, and Kubernetes binds it to a suitable Persistent Volume.

### Difference between PV and PVC?
> PV is the actual storage resource in the cluster.
> PVC is a request for storage made by a user or Pod.
>
> PVC binds to a matching PV based on size and access mode.

### What is StorageClass?
> StorageClass defines different types of storage with specific parameters like provisioner type and performance settings.
>
> It enables dynamic provisioning of Persistent Volumes.

### What is dynamic provisioning?
> Dynamic provisioning automatically creates a Persistent Volume when a PVC is created, based on the StorageClass configuration.
>
> It removes the need to manually create PVs.

### What is CSI?
> CSI stands for Container Storage Interface.
> It is a standardized interface that allows Kubernetes to integrate with different storage providers.

### What are volume types?
> Common volume types include:
>
> * emptyDir
> * hostPath
> * configMap
> * secret
> * PersistentVolumeClaim
> * NFS
> * Cloud provider volumes like AWS EBS, Azure Disk

### What is volumeMount?
> volumeMount is used inside the Pod specification to mount a volume into a container at a specific path.

Example:

```yaml
volumeMounts:
  - name: data-volume
    mountPath: /app/data
```

### What are access modes (RWO, RWX, ROX)?
> RWO (ReadWriteOnce) – Volume can be mounted as read-write by a single node.
> RWX (ReadWriteMany) – Volume can be mounted as read-write by multiple nodes.
> ROX (ReadOnlyMany) – Volume can be mounted as read-only by multiple nodes.

### What happens if Pod is deleted with PVC?
> If a Pod is deleted, the PVC remains unless explicitly deleted.
> The actual storage behavior depends on the reclaim policy of the PV:
>
> * Retain
> * Delete
> * Recycle (deprecated)

### How do you backup Kubernetes volumes?
> Backup methods include:
>
> * Taking cloud provider snapshots (like EBS snapshot)
> * Using Velero for cluster backup
> * Using storage-level backup solutions
>
> In production, we automate backups regularly.

### How do you migrate storage?
> Storage migration can be done by:
>
> * Creating a new PVC with a different StorageClass
> * Copying data using a temporary Pod
> * Taking snapshot and restoring to new storage
>
> In cloud environments, snapshot and restore is the safest method.

👉 “What is the difference between emptyDir and PVC?”
> emptyDir is temporary storage tied to Pod lifecycle.
> PVC provides persistent storage independent of Pod lifecycle.