# cis-lab
## Ingress
Artefacts of simple Ingress deployment
* ingress-cis-deploy.yaml

	File to deploy CIS to manage Ingress resource

* ingressclass.yaml

	File to deploy new IngressClass resource to map Ingress resources to CIS

* ingress.yaml

	File to deploy new simple Ingress resource to CIS

* ingress.CIS1.json

	AS3 declaration retrieved from BIG-IP post Ingress creation

* ingress.bigip.conf

	Full bigip.conf file of the CIS partition post Ingress creation

<br/>

## AS3-ConfigMap

Artefacts of AS3 ConfigMap deployment
* override-cis-deploy.yaml

	File to deploy CIS to manage AS3 ConfigMap resource, complete with a default CIS-managed partition which would not be used by this ConfigMap

* nodeport.svc.yaml

	File to deploy simple NodePort service for pre-existing DeploymentConfig, specifically labelled to work with the sample AS3 ConfigMap file

* as3.cm.yaml

    File to deploy new ConfigMap resource containing AS3 declaration whose objects match those of the sample NodePort Service

* cm.AS3CM.json

	AS3 declaration retrieved from BIG-IP post ConfigMap creation

* cm.bigip.conf

	Full bigip.conf file of the CIS partition post ConfigMap creation

<br/>

## AS3-Override

Artefacts of simple Ingress + AS3 Override deployment
* override-cis-deploy.yaml

	File to deploy CIS to manage Ingress resource with AS3 override enabled for a specific Namespace/ConfigMap tuple

* ingressclass.yaml

	File to deploy new IngressClass resource to map Ingress resources to CIS

* ingress.yaml

	File to deploy new simple Ingress resource to CIS

* override.cm.yaml

    File to deploy new ConfigMap to override the AS3 declaration of the Ingress

* override.CIS1.json

	AS3 declaration retrieved from BIG-IP post Ingress & ConfigMap creation

* override.bigip.conf

	Full bigip.conf file of the CIS partition post Ingress & ConfigMap creation

<br/>

## CRD

Artefacts of simple CRD deployment
* crd-cis-deploy.yaml

	File to deploy CIS to manage CRD resources

* vs.yaml

    File to deploy new virtualserver CRD

* crd.CIS1.json

	AS3 declaration retrieved from BIG-IP post virtualserver CRD creation

* crd.bigip.conf

	Full bigip.conf file of the CIS partition post virtualserver CRD creation