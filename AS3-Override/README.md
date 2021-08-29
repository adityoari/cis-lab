# AS3 Override

## Diagram

![AS3 Override Diagram](../images/AS3-Override.png)

## High-level Flow

1. Admin creates CIS Deployment with BIG-IP Partition name to manage and Namespace & name of the AS3 override ConfigMap
2. Kubernetes creates CIS POD which will monitor the API server
3. Admin creates IngressClass with specific name
4. Admin creates Ingress definition

    * Annotations contain VS IP address and port
    * Rules
      * Hostname of the front-end VS
      * URL Path
    * Backend Service name
    * Backend Service port
<br/><br/>

5. Admin creates ConfigMap definition

    * Namespace and name as defined in CIS Deployment
    * Labels of overrideAS3 and f5type
    * Tenant defined as CIS partition
    * Application matching Ingress AS3
    * Components overrides
<br/><br/>

6. IngressClass definition is pushed to Kubernetes API
7. Ingress and ConfigMap definitions are pushed to Kubernetes API
8. CIS POD detects new Ingress
9. CIS POD combines the new Ingress with the existing NodePort Service

    * Looks up the Namespace of the Service
    * Matches the Service name & port
    * Looks up the nodePort
<br/><br/>

10. CIS POD composes AS3 declaration to be pushed to BIG-IP

    * Tenant name is the BIG-IP Partition in CIS definition
    * Endpoint Policy
      * Name is composed of Ingress annotations: VS name and VS port
      * Rule to match Ingress definition: Hostname and URL path
      * Action to select the AS3 Pool
    * Service HTTP VS
      * Name is composed of Ingress annotations: VS name and VS port
      * IP address and port as declared in Ingress annotations
      * Pointer to AS3 Endpoint Policy
    * Pool
      * Member service addresses are Kuberenetes nodes
      * Member service port is NodePort of the Service
    * Components defined in ConfigMap overrides any of the above