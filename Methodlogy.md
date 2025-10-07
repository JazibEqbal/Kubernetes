Labels: Helps in organizing, categorizing and grouping for kubernetes objects.

Selectors: Helps to filter kubernetes objects based on their labels.

kubectl get pod -l app=color-api --> gets additional fields
kubectl get pod -l 'tier in (frontend)' --> gets additional fields

matchExpressions:
    -key: key_name
     operatior: In/NotIn/Exists/DoesNotExists
     value: ['canary']

    Best way is to add managed labels and set it to True or anything:
        matchExpressions:
        - key: managed
          operator: Exists

Annotations: Helps in adding useful information and configuration to resources.

Namespaces: improve isolation for group of resources. Basically helps in dividing resources across multiple clusters, environments.

Resource (applied at ns level), requests and limits helps us to fairly devide resources such as CPU, memory, storage as per configuration so that a single
application or namespace doesn't consume all of resorce. Request is like minimum resource needed and limit as maximum.

Probes are periodic health checks performed by kubernetes to determins the status of a container.
Types of probes: Startup, Liveness and Readiness --> avoids traffic to go into unhealthy pods and restarts pods as per configuration.

Volumes: 
  emptyDir: Pod lifecycle, defined at pod level, ephermal
  local: node lifecycle, defined at node level, persistent

  Static Provisioning: volumes are created and based on PV claims pods are allocated
  Dynamic Provisioning: PV claims are created and then volumes are created and pods are allocated.
  Retain is default persistentVolumeReclaimPolicy & Filesystem is default volumeMode.

kubectl exec -it pod_name --sh --> starting a shell within a pod
kubectl exec -it pod_name  -c container_name --sh --> starting a shell within a container from a pod which has many containers.

StatefulSet: Provides stable DNS identity with indexing. They help to create pods with a defined-index name rather than adding randome strings to pod definitions. If a pod is deleted and re-created it will use the same volume and PVC is not deleted which is bound to the pod.

Headless StatefulSet means defining a service and setting clusterIp to None which means no clusterIp will be assigned to the resource created.

ConfigMaps: Decouple and inject configurations into Pods. 
It helps us to store non sensitive data as key value pairs and decouple this data from the pod definition and lifecycle.
ConfigMaps can be referenced by environment variables or by file mounts. 
ConfigMaps size cannot exceed 1MB.
ConfigMaps and Pods must exist in the same namespace.
Config can be set as immutable.

kubectl get configmap

Secrets: Decouple and inject sensitive into Pods.
         Type Opaque and can be decrypted from base64.
           kubectl create secret generic <secret_name> --from-literal=username=<username> --from-literal=password=<password>