# vSphere 7 with kubernetes

## Yaml檔使用建議
1. gc_biuld.yaml
   
   Create Tanzu Kubernetes Cluster (Guest Cluster)
***
2. yelb_demo_gc.yaml

   Demo yelb used storageclass "gold", with PVC
***
3. yelb_demo_sc.yaml
   
   Demo pure yelb 
***
1. psp.yaml
   
   Guset Cluster RBAC


### vSphere 7 with kubernetes Login語法

1. 登入Kubernetes範例，可參考如下
```bash
  $ kubectl vsphere login --server 10.9.47.1 --vsphere-username william@vsphere.local --insecure-skip-tls-verify

  Password:
  Logged in successfully.

  You have access to the following contexts:
    10.9.47.1
    demo
    sysage
    sysdemo
    wcptest

  If the context you wish to use is not in this list, you may need to try
  logging in again later, or contact your cluster administrator.

  To change context, use `kubectl config use-context <workload name>`
```
2. 切換 Namespace 語法
```bash
  $ kubectl config use-context sysage

  Switched to context "sysage".
```
3. 查看Namespace內所有狀態語法
```bash
  $ kubectl get all
```

### Virtual Machine Class Types基本架構

Class               | CPU |Memory(GB)|Storage (GB)|Reserved CPU and Memory
--------------------|----:|---------:|-----------:|-----------------------
`guaranteed-xlarge` |  `4`|      `32`|        `16`| Yes
`best-effort-xlarge`|  `4`|      `32`|        `16`| Yes
`guaranteed-large`  |  `4`|      `16`|        `16`| Yes
`best-effort-large` |  `4`|      `16`|        `16`| Yes
`guaranteed-medium` |  `2`|       `8`|        `16`| Yes
`best-effort-medium`|  `2`|       `8`|        `16`| Yes
`guaranteed-small`  |  `2`|       `4`|        `16`| Yes
`best-effort-small` |  `2`|       `4`|        `16`| Yes
`guaranteed-xsmall` |  `2`|       `2`|        `16`| Yes
`best-effort-xsmall`|  `2`|       `2`|        `16`| Yes
