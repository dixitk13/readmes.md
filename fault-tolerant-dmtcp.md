# fault-tolerant-dmtcp
Fault Tolerant DMTCP.

Integrated DMTCP coordinator to work with zookeeper and make it fault tolerant by saving the state of the current coordinator, so that standby masters can continue to checkpoint from that particular state and single point of failure for computation is avoided.

Currently, DMTCP has a centralized coordinator that communicates with all worker nodes. The centralized nature makes it a single point of failure for the computation. One way to address is to use distributed coordinator processes with leader-election. These coordinators can share the current state using Zookeeper. Leader election also happens with these znode and a common leader is choosen amongst the available dmtcp coordinators (representing znodes) with whom the worker processes talk.

### [Fault Tolerant DMTCP](https://github.com/dixitk13/dmtcp/blob/master/Fault_tolerant_DMTCP_Coordinator_Project_Report.pdf)
The Details of Implementation are in the [report](https://github.com/dixitk13/dmtcp/blob/master/Fault_tolerant_DMTCP_Coordinator_Project_Report.pdf) and the Repository is [here](https://github.com/dixitk13/dmtcp)

### Version
1.0

created using : [Dillinger](http://dillinger.io/)
