# GitOpsによるVMデプロイのデモ
OpenShift Vitualization + OpenShift GitOpsの極簡単なデモです。
VirtualizationとGitOpsのOperatorをインストールの上、下記のコマンド実行することでArgoCDアプリケーションが設定されます。

```
oc apply -f https://raw.githubusercontent.com/KaitoInaba/ocpv-gitops/main/deployvm/apps.yaml
```

ArgoCD アプリケーション作成後の状態は下記のようになります。
* ArgoCDアプリケーション `vmdeployfromgitops` が作成されます
* Project `deployvm` が作成されます
* 上記のProject配下に2台のVM(`fedora01`,`fedora02`)が作成されます

![デプロイ結果](figure/result.png "Result")

## ご留意事項
* まっさらな環境でクイックにデプロイできることを優先しているため、VMのrootdiskはContainer Storageを指定しています = Ephemeralストレージのため再起動後ごとに初期状態に戻ります。
  実使用時はインストール済みのPVなどをrootdiskにご指定ください。
