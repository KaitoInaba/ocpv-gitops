OpenShift Vitualization + OpenShift GitOpsの極簡単なデモです。
VirtualizationとGitOpsのOperatorをインストールの上、下記のコマンド実行することでArgoCDアプリケーションが設定されます。
構成ドリフトの修正やVM削除しても戻ることなどをお示し頂くのにご利用ください。

```
oc apply -f https://raw.githubusercontent.com/KaitoInaba/ocpv-gitops/main/deployvm/apps.yaml
```

ArgoCD アプリケーション作成後の状態は下記のようになります。
* ArgoCDアプリケーション `vmdeployfromgitops` が作成されます
* Project `deployvm` が作成されます
* 上記のProject配下に2台のVM(`fedora01`,`fedora02`)が作成されます（停止状態）

![デプロイ結果](figure/result.png "Result")
