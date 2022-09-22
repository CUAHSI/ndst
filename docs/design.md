# Design Document - V 1.0


## 1. JupyterHub Server

The JupyterHub server will be configured and deployed using the Kubernetes orchestration framework in the Google Cloud Platform. It will consist of a single computing environment and will support a maximum of 10 concurrent users. Below are the hardware specifications:


|Attribute| Value|
|---|---|
|Users per Node |	2 |
|Number of Nodes	| 0 - 5|
|Guaranteed CPU	| 4|
|Guaranteed RAM	| 16|
|Total Users Supported |	10|
|Machine Type	 | E2-standard-8|
|Image Type	| Container Optimized OS|
|Persistent Disk | 20 GiB|

## 2. Shared Data (Readonly)

The NDST will also contain a read only data store that is accessible from within JupyterHub. The hardware specifications for this are listed below:

|Attribute| Value|
|---|---|
|Machine Type	 | e2-standard-2 (2 vCPUs, 8 GB memory) |
|Image Type |	Container Optimized OS|
|Boot HDD | 50 GiB |
|Data HDD | 100 GiB |
	


