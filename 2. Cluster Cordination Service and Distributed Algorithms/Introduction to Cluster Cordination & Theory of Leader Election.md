## **Terminology**

### **Node**
- A process running on a dedicated machine.

### **Cluster**
- A collection of computers/nodes connected to each other.  
- The nodes in a cluster work on the same task and typically run the same code.

## **How to Break the Work Among Nodes**

In distributed systems, work distribution among nodes is a critical challenge. Below are three approaches to achieve this:

---

### **1. Manual Distribution**
- **Approach**: Distribute the work manually and assign each node a separate task.  
- **Challenges**:  
  - This approach does not scale well.  
  - A programmatic system is necessary when dealing with thousands of tasks per second.

---

### **2. Manual Leader Election**
- **Approach**: Manually elect a leader (or master) node to:
  - Distribute tasks among the nodes.
  - Collect results from the nodes.  
- **Challenges**:
  - **Single Point of Failure**: If the master node fails, the entire cluster becomes inoperative.  
  - In large distributed systems, failure is not a matter of **if**, but **when**.  
  - Without the master node, tasks cannot be distributed, and results cannot be collected.  

---

### **3. Automatic Leader Election**
- **Approach**: Implement an algorithm for nodes to:
  - Automatically elect a leader (or master) on demand.  
  - Continuously monitor the leader's health.  
- **Key Features**:  
  - **Failover Handling**: If the leader node becomes unavailable, the remaining nodes re-elect a new leader.  
  - **Seamless Recovery**: When the old leader recovers and rejoins the cluster, it recognizes it is no longer the leader and resumes as a regular node.  

- **Advantages**:
  - Eliminates a single point of failure.  
  - Ensures high availability and fault tolerance.  
  - Enables dynamic adaptation to node failures or recoveries.  

