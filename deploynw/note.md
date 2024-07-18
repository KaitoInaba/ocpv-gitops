確認した環境（OpenShift-Gitops Operator 1.13.0 , OpenShift Virtualization Operator 4.15.2)において、既定ではArgoCDのサービスアカウントにAPIグループ： `k8s.cni.cncf.io` を操作する権限が不足しており、Network Attachment Definitionの作成などに失敗します。

ArgoCDのサービスアカウントに対しAPIグループへのRole-Bindigを作成してあげることで解消します。

1. `k8s.cni.cncf.io` に対するRoleを作成(以下作成例)

```
---
apiVersion: rbac.authorization.k8s.io/v1
kind: ClusterRole
metadata:
  name: cni-resources
rules:
- apiGroups: ["k8s.cni.cncf.io"]
  resources: ["*"]
  verbs: ["*"]
```

2. 以下のサービスアカウントに対し、上記RoleへのRole-binding作成

* kind: ServiceAccount
* name: openshift-gitops-argocd-application-controller
* namespace: openshift-gitops

