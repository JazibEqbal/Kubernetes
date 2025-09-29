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