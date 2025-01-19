After cloning the [repository](https://github.com/questdb/questdb-operator) You can generate crds from the folder [config/crd](https://github.com/questdb/questdb-operator/tree/main/config/crd) executing:
```
kubectl kustomize . > default_crds.yaml 
```
and it will generate the CRDs in that file.
Then you can apply them: 
```
kubectl apply -f default_crds.yaml
```