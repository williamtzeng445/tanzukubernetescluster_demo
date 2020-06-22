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
4. psp.yaml
   
   Guset Cluster RBAC
***
5. kube-scan-lb.yaml

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


### OCARINE
<p align="center">
  <img src="octarine_logo.png">
</p>

#### Kube-Scan

通過kube-scan立即發現您的Kubernetes工作負載是否存在風險

- 在每個開發人員的控制下，都有30多種安全設置
- 您需要成為Kubernetes專家才能了解最終配置是否會對您的集群帶來高風險。
- 只需對單個文件進行一次更改，就可以打開整個Kubernetes集群以攻擊，洩漏機密，冒險機密數據，或者不經意地允許公眾訪問私有服務。

Octarine相信使每個人都容易獲得安全性。Kube-scan是一種快速且易於運行的開源安全風險評估工具，可立即告訴您Kubernetes集群的安全狀態。

安裝方式
```bash
kubectl apply -f kube-scan-lb.yaml
```