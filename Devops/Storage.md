# Storage

## Ceph

| **Component**       | **Purpose**                          | **Use Case**                             |
|---------------------|--------------------------------------|------------------------------------------|
| Ceph-mgr            | Monitoring and management            | Cluster health, dashboard, orchestration |
| Ceph-mds            | File system metadata management      | CephFS                                   |
| RADOS Gateway (RGW) | Object storage interface             | S3/Swift-compatible storage              |
| RBD                 | Block storage interface              | VM disks, databases                      |
| CephFS              | Distributed file system              | Shared storage for HPC, big data         |
| Cephadm             | Orchestration and deployment         | Simplifies cluster setup and upgrades    |
| Rook                | Kubernetes-native Ceph orchestration | Kubernetes storage backend               |
| Dashboard           | Web interface for management         | Monitoring and configuration             |
| Prometheus Module   | Metrics for monitoring               | Cluster performance analytics            |
| iSCSI Gateway       | iSCSI access to Ceph storage         | Windows or legacy iSCSI systems          |
| RBD Mirror          | Replicates RBD images                | Disaster recovery, backups               |
| BlueStore           | Storage backend                      | Efficient storage management             |

| **Component**           | **Installable?** | **How to Install/Deploy**                                                               |
|-------------------------|------------------|-----------------------------------------------------------------------------------------|
| **Ceph-mgr**            | Yes              | Deployed automatically by Cephadm or as part of a manual Ceph cluster installation.     |
| **Ceph-mds**            | Yes              | Installed if using CephFS. Requires configuration via Cephadm or manual setup.          |
| **RADOS Gateway (RGW)** | Yes              | Installed to provide object storage via S3/Swift APIs. Deploy with Cephadm or manually. |
| **RBD**                 | No (Integrated)  | Integrated into Ceph. Accessible after deploying Ceph-osd and Ceph-mgr.                 |
| **CephFS**              | No (Integrated)  | Enabled after deploying Ceph-mds. Requires client-side setup to mount the file system.  |
| **Cephadm**             | Yes              | Installable tool for automating the deployment of a Ceph cluster.                       |
| **Rook**                | Yes              | Deployable as a Kubernetes operator. Installation involves Helm or YAML files.          |
| **Dashboard**           | No (Integrated)  | Enabled by default in Ceph-mgr. Accessible after setting up the Ceph cluster.           |
| **Prometheus Module**   | No (Integrated)  | Integrated with Ceph-mgr. Requires enabling the module via CLI.                         |
| **iSCSI Gateway**       | Yes              | Installed if you need iSCSI access. Deploy manually or via Cephadm.                     |
| **RBD Mirror**          | Yes              | Deployed for cross-cluster RBD image replication. Configure with Cephadm or manually.   |
| **BlueStore**           | No (Integrated)  | Default backend for Ceph OSDs. Automatically used when deploying Ceph-osd.              |

Components Installed Automatically with Ceph
When you deploy Ceph using tools like Cephadm, some components are installed and configured automatically:

* **Ceph-mgr (Manager):** For monitoring and management.
* **Ceph-mon (Monitor):** For cluster state tracking.
* **Ceph-osd (Object Storage Daemon):** For managing storage devices.
* **Dashboard:** For web-based management (via Ceph-mgr).
* **Prometheus Module:** For monitoring metrics (via Ceph-mgr).

Manually Installable Components
If you are not using automation tools like Cephadm or Rook, you can manually install the following components on
different nodes in your cluster:

* **Ceph-mgr:** For cluster monitoring and additional services.
* **Ceph-mds:** Required only for CephFS.
* **RADOS Gateway (RGW):** For object storage APIs (e.g., S3, Swift).
* **iSCSI Gateway:** For iSCSI protocol support.
* **RBD Mirror:** For asynchronous replication between Ceph clusters.

### Rook + K8s

Components Deployed by Rook for Ceph:

* Monitors (Ceph-mon): Tracks the cluster state and ensures consistency.
* OSDs (Ceph-osd): Manages the physical disks and stores data.
* Manager (Ceph-mgr): Provides management and monitoring capabilities.
* RADOS Gateway (RGW): Provides object storage using S3 or Swift APIs.
* CephFS: Enables shared POSIX-compliant file systems.
* RBD: Offers block storage for high-performance workloads.
