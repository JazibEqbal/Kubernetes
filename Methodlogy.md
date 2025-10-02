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

kubectl exec -it pod_name --sh --> starting a shell within a pod
kubectl exec -it pod_name  -c container_name --sh --> starting a shell within a container from a pod which has many containers