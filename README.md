
# Installation

## Install ArgoCD
Login in OCP instance:
```bash 
oc login -u $USER $OCP_HOST
```

Apply the GitOps operator
```bash
oc apply -f operators/openshift-gitops.yaml
```

Get the ArgoCD route: 
```bash
oc get route -A | grep openshift-gitops-server | awk '{print $3}'
```

Finally, get the ArgoCD password:
```bash
oc -n openshift-gitops get secret openshift-gitops-cluster -o json | jq -r '.data["admin.password"]' | base64 -d
```

Once the ArgoCD is running, we can execute our bootstrap application which will deploy all the necessary to have a KeyCloak instance:
```bash

```