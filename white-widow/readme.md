``` sh
 kubectl taint nodes --all node-role.kubernetes.io/control-plane-
 kubectl apply -f https://github.com/kubevirt/kubevirt/releases/download/${RELEASE}/kubevirt-operator.yaml
 kubectl apply -f https://github.com/kubevirt/kubevirt/releases/download/${RELEASE}/kubevirt-cr.yaml
 kubectl -n kubevirt wait kv kubevirt --for condition=Available
 
 kubectl get pods -n kubevirt
    NAME                               READY   STATUS    RESTARTS   AGE
    virt-api-7fb5d599cc-hslp8          1/1     Running   0          57m
    virt-controller-6d594d9b54-gkd8c   1/1     Running   0          56m
    virt-controller-6d594d9b54-lmhph   1/1     Running   0          56m
    virt-handler-bcb7w                 1/1     Running   0          56m
    virt-operator-747d64c764-c544b     1/1     Running   0          57m
    virt-operator-747d64c764-w8tgk     1/1     Running   0          57m
 
 kubectl explain kubevirt
 kubectl describe crd kubevirts.kubevirt.io
 kubectl describe crd virtualmachines.kubevirt.io
 
 
 kubectl api-resources -n kubevirt
 kubectl get all -n kubevirt
    Warning: kubevirt.io/v1 VirtualMachineInstancePresets is now deprecated and will be removed in v2.
    NAME                                   READY   STATUS    RESTARTS   AGE
    pod/virt-api-7fb5d599cc-hslp8          1/1     Running   0          61m
    pod/virt-controller-6d594d9b54-gkd8c   1/1     Running   0          61m
    pod/virt-controller-6d594d9b54-lmhph   1/1     Running   0          61m
    pod/virt-handler-bcb7w                 1/1     Running   0          61m
    pod/virt-operator-747d64c764-c544b     1/1     Running   0          62m
    pod/virt-operator-747d64c764-w8tgk     1/1     Running   0          62m

    NAME                                  TYPE        CLUSTER-IP       EXTERNAL-IP   PORT(S)   AGE
    service/kubevirt-operator-webhook     ClusterIP   10.103.243.119   <none>        443/TCP   61m
    service/kubevirt-prometheus-metrics   ClusterIP   10.100.154.18    <none>        443/TCP   61m
    service/virt-api                      ClusterIP   10.105.201.229   <none>        443/TCP   61m
    service/virt-exportproxy              ClusterIP   10.96.60.141     <none>        443/TCP   61m

    NAME                          DESIRED   CURRENT   READY   UP-TO-DATE   AVAILABLE   NODE SELECTOR            AGE
    daemonset.apps/virt-handler   1         1         1       1            1           kubernetes.io/os=linux   61m

    NAME                              READY   UP-TO-DATE   AVAILABLE   AGE
    deployment.apps/virt-api          1/1     1            1           61m
    deployment.apps/virt-controller   2/2     2            2           61m
    deployment.apps/virt-operator     2/2     2            2           62m

    NAME                                         DESIRED   CURRENT   READY   AGE
    replicaset.apps/virt-api-7fb5d599cc          1         1         1       61m
    replicaset.apps/virt-controller-6d594d9b54   2         2         2       61m
    replicaset.apps/virt-operator-747d64c764     2         2         2       62m

    NAME                            AGE   PHASE
    kubevirt.kubevirt.io/kubevirt   62m   Deployed


 
 kubectl create -f vmi.yml
  kubectl get vmis
    NAME              AGE   PHASE     IP            NODENAME            READY
    testvmi-nocloud   58m   Running   10.244.0.14   node1.white-widow   True
    
 kubectl delete vmi testvmi-nocloud
```
