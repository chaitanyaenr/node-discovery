# Node-feature-discovery
We can use this feature to add labels to the nodes to advertise hardware features.
 
### Run 
```
$ cd node-feature-discovery
$ ./node_feature_discovery.sh <TYPE>
TYPE can be a job or daemonset
```
This scripts supports running the node-feature-discovery as a job and daemonset. It ensures that each node has a pod running on it by using a privileged serviceaccount after creating a role and binding the default user to view the pods in the node-feature-discovery namespace. The nodes will get labeled with the hardware features available on the node. Following are the labels which got added to the nodes after a sample run:

```
$ oc get nodes -o json | jq .items[].metadata.labels 

{
  "beta.kubernetes.io/arch": "amd64",
  "beta.kubernetes.io/instance-type": "t2.medium",
  "beta.kubernetes.io/os": "linux",
  "failure-domain.beta.kubernetes.io/region": "us-west-2",
  "failure-domain.beta.kubernetes.io/zone": "us-west-2b",
  "kubernetes.io/hostname": "ip-172-31-1-23.us-west-2.compute.internal",
  "node.alpha.kubernetes-incubator.io/nfd-cpuid-AESNI": "true",
  "node.alpha.kubernetes-incubator.io/nfd-cpuid-AVX": "true",
  "node.alpha.kubernetes-incubator.io/nfd-cpuid-AVX2": "true",
  "node.alpha.kubernetes-incubator.io/nfd-cpuid-BMI1": "true",
  "node.alpha.kubernetes-incubator.io/nfd-cpuid-BMI2": "true",
  "node.alpha.kubernetes-incubator.io/nfd-cpuid-CLMUL": "true",
  "node.alpha.kubernetes-incubator.io/nfd-cpuid-CMOV": "true",
  "node.alpha.kubernetes-incubator.io/nfd-cpuid-CX16": "true",
  "node.alpha.kubernetes-incubator.io/nfd-cpuid-ERMS": "true",
  "node.alpha.kubernetes-incubator.io/nfd-cpuid-F16C": "true",
  "node.alpha.kubernetes-incubator.io/nfd-cpuid-FMA3": "true",
  "node.alpha.kubernetes-incubator.io/nfd-cpuid-LZCNT": "true",
  "node.alpha.kubernetes-incubator.io/nfd-cpuid-MMX": "true",
  "node.alpha.kubernetes-incubator.io/nfd-cpuid-MMXEXT": "true",
  "node.alpha.kubernetes-incubator.io/nfd-cpuid-NX": "true",
  "node.alpha.kubernetes-incubator.io/nfd-cpuid-POPCNT": "true",
  "node.alpha.kubernetes-incubator.io/nfd-cpuid-RDRAND": "true",
  "node.alpha.kubernetes-incubator.io/nfd-cpuid-RDTSCP": "true",
  "node.alpha.kubernetes-incubator.io/nfd-cpuid-SSE": "true",
  "node.alpha.kubernetes-incubator.io/nfd-cpuid-SSE2": "true",
  "node.alpha.kubernetes-incubator.io/nfd-cpuid-SSE3": "true",
  "node.alpha.kubernetes-incubator.io/nfd-cpuid-SSE4.1": "true",
  "node.alpha.kubernetes-incubator.io/nfd-cpuid-SSE4.2": "true",
  "node.alpha.kubernetes-incubator.io/nfd-cpuid-SSSE3": "true",
  "node.alpha.kubernetes-incubator.io/node-feature-discovery.version": "v0.1.0-dirty",
  "region": "primary",
  "zone": "default"
}
{
  "beta.kubernetes.io/arch": "amd64",
  "beta.kubernetes.io/instance-type": "t2.medium",
  "beta.kubernetes.io/os": "linux",
  "failure-domain.beta.kubernetes.io/region": "us-west-2",
  "failure-domain.beta.kubernetes.io/zone": "us-west-2b",
  "kubernetes.io/hostname": "ip-172-31-9-21.us-west-2.compute.internal",
  "node.alpha.kubernetes-incubator.io/nfd-cpuid-AESNI": "true",
  "node.alpha.kubernetes-incubator.io/nfd-cpuid-AVX": "true",
  "node.alpha.kubernetes-incubator.io/nfd-cpuid-AVX2": "true",
  "node.alpha.kubernetes-incubator.io/nfd-cpuid-BMI1": "true",
  "node.alpha.kubernetes-incubator.io/nfd-cpuid-BMI2": "true",
  "node.alpha.kubernetes-incubator.io/nfd-cpuid-CLMUL": "true",
  "node.alpha.kubernetes-incubator.io/nfd-cpuid-CMOV": "true",
  "node.alpha.kubernetes-incubator.io/nfd-cpuid-CX16": "true",
  "node.alpha.kubernetes-incubator.io/nfd-cpuid-ERMS": "true",
  "node.alpha.kubernetes-incubator.io/nfd-cpuid-F16C": "true",
  "node.alpha.kubernetes-incubator.io/nfd-cpuid-FMA3": "true",
  "node.alpha.kubernetes-incubator.io/nfd-cpuid-LZCNT": "true",
  "node.alpha.kubernetes-incubator.io/nfd-cpuid-MMX": "true",
  "node.alpha.kubernetes-incubator.io/nfd-cpuid-MMXEXT": "true",
  "node.alpha.kubernetes-incubator.io/nfd-cpuid-NX": "true",
  "node.alpha.kubernetes-incubator.io/nfd-cpuid-POPCNT": "true",
  "node.alpha.kubernetes-incubator.io/nfd-cpuid-RDRAND": "true",
  "node.alpha.kubernetes-incubator.io/nfd-cpuid-RDTSCP": "true",
  "node.alpha.kubernetes-incubator.io/nfd-cpuid-SSE": "true",
  "node.alpha.kubernetes-incubator.io/nfd-cpuid-SSE2": "true",
  "node.alpha.kubernetes-incubator.io/nfd-cpuid-SSE3": "true",
  "node.alpha.kubernetes-incubator.io/nfd-cpuid-SSE4.1": "true",
  "node.alpha.kubernetes-incubator.io/nfd-cpuid-SSE4.2": "true",
  "node.alpha.kubernetes-incubator.io/nfd-cpuid-SSSE3": "true",
  "node.alpha.kubernetes-incubator.io/node-feature-discovery.version": "v0.1.0-dirty",
  "node_role": "node",
  "pbench_role": "agent",
  "region": "primary",
  "zone": "default"
}

```
