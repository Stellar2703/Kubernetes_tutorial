```
kubectl get namespace
```

![[Pasted image 20240918223142.png]]

  **Kube-system**
- Do NOT create or modify in kube-system
- They run System processes
- Master and Kubectl processes are present in it
 **kube-public**
- publicely accessible data
- A configmap, which contains cluster information
**kube-node-release**
- heartbeats of nodes
- each node has associated lease object in namespace
- determines the availability of nodes
**Default**
- Resources that we create are located here
- 