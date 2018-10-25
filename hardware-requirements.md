# OS  
`` Ubuntu 16.04.05 LTS `` 

# Hardware Requirements 

## Registry
  **No. of VMs** : 1 (2 for optimal performance)  
  **VCores** :8 (in total)  
  **RAM** : 16GB  (in total)  
  **Hard disk** : 260GB (60GB for basic installation + 200 GB for the store service)
  
## Workflow Execution

### Standalone mode

  **No. of VMs** : 1  
  **VCores** : 4  
  **RAM** : 16GB  
  **Hard disk** : 100GB  

### Cluster enabled
  **No. of VMs** : 3-11 (depends on how spread out you want the services)
 
#### Executor and NFS
  **VCores** : 4
  **RAM** : 4GB
  **Hard disk** : 40GB + at least 400GB for NFS share, expandable for scaling

#### Cluster scheduler and manager (at least 1)
  **VCores** : 2
  **RAM** : 2GB
  **Hard disk** : 20GB

#### Cluster Normal Nodes (at least 1, but the more, the better)
  **VCores** : 2 (but the more the better)
  **RAM** : 2GB (but the more the better)
  **Hard disk** : 20GB

#### Cluster Heavy Nodes (at least 1, if your docker images are larger than 1GB)
  **VCores** : 4 (but the more the better)
  **RAM** : 4GB (but the more the better)
  **Hard disk** : 200GB (but the more, the better)

#### Cluster Monitoring (1, optional)
  **VCores** : 4
  **RAM** : 4GB (but the more the better
  **Hard disk** : 20GB

#### Docker Private Registry (1)
  **VCores** : 2
  **RAM** : 4GB (but the more the better
  **Hard disk** : 100GB
